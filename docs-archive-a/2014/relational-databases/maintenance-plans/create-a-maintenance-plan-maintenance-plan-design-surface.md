---
title: 建立維護計畫 (維護計畫設計介面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77e347720824198ba7d6abaddedd7a581ace98a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598361"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a><span data-ttu-id="a4ee3-102">建立維護計畫 (維護計畫設計介面)</span><span class="sxs-lookup"><span data-stu-id="a4ee3-102">Create a Maintenance Plan (Maintenance Plan Design Surface)</span></span>
  <span data-ttu-id="a4ee3-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的維護計畫設計介面，建立單一伺服器或多伺服器維護計畫。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Design Surface in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a4ee3-104">雖然 **[維護計畫精靈]** 最適用於建立基本的維護計畫，但使用設計介面建立計畫時可讓您利用加強的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-104">While the **Maintenance Plan Wizard** is best for creating basic maintenance plans, creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="a4ee3-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a4ee3-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a4ee3-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="a4ee3-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a4ee3-108">安全性</span><span class="sxs-lookup"><span data-stu-id="a4ee3-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="a4ee3-109">使用維護計畫設計介面建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="a4ee3-109">Creating a maintenance plan using the Maintenance Plan Design Surface</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a4ee3-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="a4ee3-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a4ee3-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="a4ee3-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a4ee3-112">若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-112">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="a4ee3-113">多伺服器維護計畫必須在主要伺服器上建立和維護。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-113">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="a4ee3-114">您可以在目標伺服器上檢視這些計畫，但不能加以維護。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-114">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="a4ee3-115">**db_ssisadmin** 角色和 **dc_admin** 角色的成員可以將其權限提高為 **系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-115">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="a4ee3-116">能夠提高權限是因為這些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝；這些封裝可藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 **sysadmin** 安全性內容由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-116">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="a4ee3-117">若要在執行維護計畫、資料收集組和其他 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時預防此權限提高，請將執行封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業設為使用有限權限的 Proxy 帳戶，或是只將 **系統管理員** 成員加入 **db_ssisadmin** 和 **dc_admin** 角色。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-117">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a4ee3-118">Security</span><span class="sxs-lookup"><span data-stu-id="a4ee3-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a4ee3-119">權限</span><span class="sxs-lookup"><span data-stu-id="a4ee3-119">Permissions</span></span>  
 <span data-ttu-id="a4ee3-120">若要建立或管理維護計畫，您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-120">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="a4ee3-121">只有在使用者是 **sysadmin** 固定伺服器角色的成員時，[物件總管] 才會顯示 **[維護計畫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-121">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-design-surface"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a4ee3-122">使用維護計畫設計介面</span><span class="sxs-lookup"><span data-stu-id="a4ee3-122">Using Maintenance Plan Design Surface</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="a4ee3-123">若要建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="a4ee3-123">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="a4ee3-124">在 [物件總管] 中，按一下加號以展開您要建立維護計畫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-124">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="a4ee3-125">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-125">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="a4ee3-126">以滑鼠右鍵按一下 [維護計畫] 資料夾，然後選取 [新增維護計畫]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-126">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="a4ee3-127">在 **[新增維護計畫]** 對話方塊中的 **[名稱]** 方塊，輸入計畫的名稱，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-127">In the **New Maintenance Plan** dialog box, in the **Name** box, type a name for the plan and click **OK**.</span></span> <span data-ttu-id="a4ee3-128">這會開啟工具箱和 _maintenance_plan_name_ [設計] 介面，並在主要方格中建立預設的 [子計畫_1] 子計畫。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-128">This opens the  Toolbox and the _maintenance_plan_name_ **[Design]** surface with the **Subplan_1** subplan created in the main grid.</span></span>  
  
     <span data-ttu-id="a4ee3-129">設計空間的標頭中有下列選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-129">The following options are available in the design space's header.</span></span>  
  
     <span data-ttu-id="a4ee3-130">**加入子計畫**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-130">**Add Subplan**</span></span>  
     <span data-ttu-id="a4ee3-131">新增可設定的子計畫。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-131">Adds a subplan that you can configure.</span></span>  
  
     <span data-ttu-id="a4ee3-132">**子計畫屬性**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-132">**Subplan Properties**</span></span>  
     <span data-ttu-id="a4ee3-133">在主要方格中，顯示選定子計畫的 [子計畫屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-133">Displays the **Subplan Properties** dialog box for the selected subplan in the main grid.</span></span> <span data-ttu-id="a4ee3-134">或者，請按兩下方格中的子計畫，顯示 [子計畫屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-134">Alternately, double-click a subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="a4ee3-135">如需有關此對話方塊的詳細資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-135">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-136">**刪除選取的子計畫**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-136">**Delete Selected Subplan**</span></span>  
     <span data-ttu-id="a4ee3-137">刪除選取的子計畫。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-137">Deletes the selected subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-138">**子計畫排程**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-138">**Subplan Schedule**</span></span>  
     <span data-ttu-id="a4ee3-139">顯示選定子計畫的 [新增作業排程] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-139">Displays the **New Job Schedule** dialog box for the selected subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-140">**移除排程**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-140">**Remove Schedule**</span></span>  
     <span data-ttu-id="a4ee3-141">從選取的子計畫移除排程。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-141">Removes a schedule from the selected subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-142">**管理連線**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-142">**Manage Connections**</span></span>  
     <span data-ttu-id="a4ee3-143">顯示 [管理連接] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-143">Displays the **Manage Connections** dialog box.</span></span> <span data-ttu-id="a4ee3-144">用於將其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連接加入維護計畫。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-144">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="a4ee3-145">如需有關此對話方塊的詳細資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-145">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-146">**報表與記錄**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-146">**Reporting and Logging**</span></span>  
     <span data-ttu-id="a4ee3-147">顯示 [報表與記錄] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-147">Displays the **Reporting and Logging** dialog box.</span></span> <span data-ttu-id="a4ee3-148">如需有關此對話方塊的詳細資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-148">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-149">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-149">**Servers**</span></span>  
     <span data-ttu-id="a4ee3-150">顯示 [伺服器] 對話方塊，用來選取將執行子計畫工作的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-150">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="a4ee3-151">只有多伺服器環境中的主要伺服器才會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-151">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="a4ee3-152">如需詳細資訊，請參閱[建立多伺服器環境](../../ssms/agent/create-a-multiserver-environment.md)和[維護計畫 &#40;Servers&#41;](maintenance-plan-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-152">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) and [Maintenance Plan &#40;Servers&#41;](maintenance-plan-servers.md).</span></span>  
  
     <span data-ttu-id="a4ee3-153">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-153">**Name**</span></span>  
     <span data-ttu-id="a4ee3-154">顯示維護計畫名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-154">Display the maintenance plan name.</span></span> <span data-ttu-id="a4ee3-155">針對新的維護計畫，名稱會在維護計畫設計師開啟之前，於對話方塊中指定。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-155">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="a4ee3-156">若要重新命名維護計畫，請以滑鼠右鍵按一下物件總管中的計畫，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-156">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="a4ee3-157">**說明**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-157">**Description**</span></span>  
     <span data-ttu-id="a4ee3-158">檢視或指定維護計畫的描述。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-158">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="a4ee3-159">描述的最大長度是 512 個字元。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-159">The maximum length for a description is 512 characters.</span></span>  
  
     <span data-ttu-id="a4ee3-160">**設計師介面**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-160">**Designer Surface**</span></span>  
     <span data-ttu-id="a4ee3-161">設計維護計畫並予以維護。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-161">Design and maintain maintenance plans.</span></span> <span data-ttu-id="a4ee3-162">使用設計師介面即可將維護工作加入計畫、從計畫中移除工作、指定工作間的優先順序連結以及指出工作分支和平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-162">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
     <span data-ttu-id="a4ee3-163">兩個工作間的優先順序連結會建立工作間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-163">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="a4ee3-164">只有在第一個工作 (「前導工作」) 的執行結果符合指定的準則時，才會執行第二個工作 (「相依工作」)。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-164">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="a4ee3-165">一般而言，指定的執行結果會是 **[成功]** 、 **[失敗]** 或 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-165">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="a4ee3-166">如需詳細資訊，請參閱以下的步驟 **8** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-166">For more information, see step **8** below.</span></span>  
  
5.  <span data-ttu-id="a4ee3-167">在設計空間的標頭中，按兩下 [子計畫_1]，然後在 [子計畫屬性] 對話方塊中輸入子計畫的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-167">In the design space's header, double-click **Subplan_1** and enter a name and description for the subplan in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-168">**[子計畫屬性]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-168">The following options are available in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-169">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-169">**Name**</span></span>  
     <span data-ttu-id="a4ee3-170">子計畫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-170">The name of the subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-171">**說明**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-171">**Description**</span></span>  
     <span data-ttu-id="a4ee3-172">子計畫的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-172">A brief description of the subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-173">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-173">**Schedule**</span></span>  
     <span data-ttu-id="a4ee3-174">指出將執行子計畫的排程。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-174">Indicates on what schedule the subplan will be run.</span></span> <span data-ttu-id="a4ee3-175">按一下 **[子計畫排程]** 以開啟 **[新增作業排程]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-175">Click **Subplan Schedule** to open the **New Job Schedule** dialog box.</span></span> <span data-ttu-id="a4ee3-176">按一下 **[移除排程]** ，從子計畫中刪除排程。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-176">Click **Remove Schedule** to delete the schedule from the subplan.</span></span>  
  
     <span data-ttu-id="a4ee3-177">**執行身分** 清單</span><span class="sxs-lookup"><span data-stu-id="a4ee3-177">**Run as** list</span></span>  
     <span data-ttu-id="a4ee3-178">選取要用來執行此子工作的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-178">Select the account to use to run this subtask.</span></span>  
  
6.  <span data-ttu-id="a4ee3-179">按一下 **[子計畫排程]** ，在 **[新增作業排程]** 對話方塊中輸入排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-179">Click **Subplan Schedule** to enter schedule details in the **New Job Schedule** dialog box.</span></span>  
  
7.  <span data-ttu-id="a4ee3-180">若要建立子計畫，請從 **[工具箱]** 將工作流程元素拖放至計畫設計介面。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-180">To build the subplan, drag and drop task flow elements from the **Toolbox** to the plan design surface.</span></span> <span data-ttu-id="a4ee3-181">按兩下工作以開啟要設定工作選項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-181">Double-click tasks to open dialog boxes to configure the task options.</span></span>  
  
     <span data-ttu-id="a4ee3-182">**[工具箱]** 中有下列維護計畫工作：</span><span class="sxs-lookup"><span data-stu-id="a4ee3-182">The following maintenance plan tasks are available in the **Toolbox**:</span></span>  
  
    -   <span data-ttu-id="a4ee3-183">**備份資料庫工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-183">**Back up Database Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-184">**檢查資料庫完整性工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-184">**Check Database Integrity Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-185">**執行 SQL Server Agent 作業工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-185">**Execute SQL Server Agent Job Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-186">**執行 T-SQL 陳述式工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-186">**Execute T-SQL Statement Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-187">**記錄清除工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-187">**History Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-188">**維護清除工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-188">**Maintenance Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-189">**通知操作員工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-189">**Notify Operator Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-190">**重建索引工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-190">**Rebuild Index Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-191">**重新組織索引工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-191">**Reorganize Index Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-192">**壓縮資料庫工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-192">**Shrink Database Task**</span></span>  
  
    -   <span data-ttu-id="a4ee3-193">**更新統計資料工作**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-193">**Update Statistics Task**</span></span>  
  
     <span data-ttu-id="a4ee3-194">若要將工作加入 **[工具箱]** 中：</span><span class="sxs-lookup"><span data-stu-id="a4ee3-194">To add tasks to the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="a4ee3-195">在 **[工具]** 功能表中按一下 **[選擇工具箱項目]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-195">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="a4ee3-196">選取您要顯示在 **[工具箱]** 中的工具，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-196">Select the tools you want to appear in the **Toolbox**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a4ee3-197">將維護計畫工作加入 **[工具箱]** 之後，這些工作也會出現在 **[維護計畫精靈]** 中。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-197">Adding maintenance plan tasks to the **Toolbox** also makes them available in the **Maintenance Plan Wizard**.</span></span> <span data-ttu-id="a4ee3-198">如需上述個別工作的詳細資訊，請參閱 [啟動維護計畫精靈](use-the-maintenance-plan-wizard.md#SSMSProcedure) 下的 **使用維護計畫精靈**。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-198">For more information on the individual tasks above, see [Using Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md#SSMSProcedure) under **Start the Maintenance Plan Wizard**.</span></span>  
  
8.  <span data-ttu-id="a4ee3-199">若要定義工作之間的工作流程：</span><span class="sxs-lookup"><span data-stu-id="a4ee3-199">To define a workflow between tasks:</span></span>  
  
    1.  <span data-ttu-id="a4ee3-200">以滑鼠右鍵按一下前導工作，然後選取 [加入優先順序條件約束]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-200">Right-click the precedent task and select **Add Precedence Constraint**.</span></span>  
  
    2.  <span data-ttu-id="a4ee3-201">在 **[控制流程]** 對話方塊中的 **[到]** 清單，選取相依工作，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-201">In the **Control Flow** dialog box, in the **To** list, select the dependent task and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="a4ee3-202">按兩下這兩個工作之間的連接子以開啟 **[優先順序條件約束編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-202">Double click the connector between the two tasks to open the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="a4ee3-203">**[優先順序條件約束編輯器]** 對話方塊中有下列選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-203">The following options are available in the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="a4ee3-204">**條件約束選項**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-204">**Constraint option**</span></span>  
         <span data-ttu-id="a4ee3-205">定義條件約束在兩個工作之間的工作方式。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-205">Defines how a constraint works between two tasks.</span></span>  
  
         <span data-ttu-id="a4ee3-206">**評估作業**  清單</span><span class="sxs-lookup"><span data-stu-id="a4ee3-206">**Evaluation operation**  list</span></span>  
         <span data-ttu-id="a4ee3-207">指定優先順序條件約束所使用的評估作業。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-207">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="a4ee3-208">這些作業有：[條件約束]、[運算式]、[運算式與條件約束]，以及 [運算式或條件約束]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-208">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
         <span data-ttu-id="a4ee3-209">**值** 清單</span><span class="sxs-lookup"><span data-stu-id="a4ee3-209">**Value** list</span></span>  
         <span data-ttu-id="a4ee3-210">指定條件約束值：[成功]、[失敗] 或 [完成]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-210">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="a4ee3-211">**[成功]** 是預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-211">**Success** is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a4ee3-212">優先順序條件約束線條若是綠色代表 [成功]、紅色代表 [失敗]，而藍色代表 [完成]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-212">The precedence constraint line is green for **Success**, red for **Failure**, and blue for **Completion**.</span></span>  
  
         <span data-ttu-id="a4ee3-213">**運算式**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-213">**Expression**</span></span>  
         <span data-ttu-id="a4ee3-214">如果使用的是 [運算式]、[運算式與條件約束] 或 [運算式或條件約束] 作業，請鍵入運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-214">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression.</span></span> <span data-ttu-id="a4ee3-215">運算式必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-215">The expression must evaluate to a Boolean.</span></span>  
  
         <span data-ttu-id="a4ee3-216">**Test**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-216">**Test**</span></span>  
         <span data-ttu-id="a4ee3-217">驗證運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-217">Validate the expression.</span></span>  
  
         <span data-ttu-id="a4ee3-218">**多個條件約束**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-218">**Multiple constraints**</span></span>  
         <span data-ttu-id="a4ee3-219">定義多個條件約束如何交互操作，以控制受條件約束之工作的執行。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-219">Define how multiple constraints interoperate to control the execution of the constrained task.</span></span>  
  
         <span data-ttu-id="a4ee3-220">**邏輯 AND**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-220">**Logical AND**</span></span>  
         <span data-ttu-id="a4ee3-221">選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-221">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="a4ee3-222">所有運算式都必須評估為 True。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-222">All constraints must evaluate to True.</span></span> <span data-ttu-id="a4ee3-223">這個選項是預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-223">This option is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a4ee3-224">此種類型的優先順序條件約束會顯示為綠色、紅色或藍色的實線。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-224">This type of precedence constraint appears as a solid green, red, or blue line.</span></span>  
  
         <span data-ttu-id="a4ee3-225">**邏輯 OR**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-225">**Logical OR**</span></span>  
         <span data-ttu-id="a4ee3-226">選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-226">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="a4ee3-227">必須至少有一個條件約束評估為 True。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-227">At least one constraint must evaluate to True.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a4ee3-228">此種類型的優先順序條件約束會顯示為綠色、紅色或藍色的虛線。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-228">This type of precedence constraint appears as a dotted green, red, or blue line.</span></span>  
  
9. <span data-ttu-id="a4ee3-229">若要新增其他子計畫，其中包含依不同排程執行的工作，請按一下工具列上的 **[加入子計畫]** ，以開啟 **[子計畫屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-229">To add another subplan that contains tasks run on a different schedule, click **Add Subplan** on the toolbar to open the **Subplan Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="a4ee3-230">若要新增不同伺服器的連接：</span><span class="sxs-lookup"><span data-stu-id="a4ee3-230">To add connections to different servers:</span></span>  
  
    1.  <span data-ttu-id="a4ee3-231">在設計空間的工具列中，按一下 **[管理連接]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-231">In the design space's toolbar, click **Manage Connections**.</span></span>  
  
    2.  <span data-ttu-id="a4ee3-232">在 **[管理連接]** 對話方塊中，按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-232">In the **Manage Connections** dialog box, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="a4ee3-233">在 **[連接屬性]** 對話方塊的 **[連接名稱]** 方塊中，輸入正在建立的連接名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-233">In the **Connection Properties** dialog box, in the **Connection name** box, enter the name of the connection you are creating.</span></span>  
  
    4.  <span data-ttu-id="a4ee3-234">在 [指定下列內容以連接到 SQL Server 資料] 下的 [選取或輸入伺服器名稱] 方塊中，輸入要使用的 SQL Server 名稱，或按一下省略符號 **(...)** ，然後在 [SQL Server] 對話方塊中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-234">Under **Specify the following to connect to SQL Server data**, in the **Select or enter a server name** box, either enter the name of the SQL server you want to use or click the ellipsis **(...)** and select a server in the **SQL Server** dialog box.</span></span> <span data-ttu-id="a4ee3-235">如果您從 **[SQL Server]** 對話方塊中選取伺服器，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-235">If you select a server from the **SQL Server** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="a4ee3-236">在 **[輸入登入伺服器的資訊]** 底下，選取 **[使用 Windows NT 整合式安全性]** 或 **[使用特定的使用者名稱和密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-236">Under **Enter information to log on to the server**, select either **Use Windows NT Integrated security** or **Use a specific user name and password**.</span></span> <span data-ttu-id="a4ee3-237">如果您選擇使用特定的使用者名稱和密碼，請在 **[使用者名稱]** 和 **[密碼]** 方塊中分別輸入該資訊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-237">If you elect to use a specific user name and password, enter that information in the **User name** and **Password** boxes, respectively.</span></span>  
  
    6.  <span data-ttu-id="a4ee3-238">在 **[連接屬性]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-238">In the **Connection Properties** dialog box, click **OK**.</span></span>  
  
    7.  <span data-ttu-id="a4ee3-239">在 **[管理連接]** 對話方塊中，按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-239">In the **Manage Connections** dialog box, click **Close**.</span></span>  
  
11. <span data-ttu-id="a4ee3-240">若要指定報表選項：</span><span class="sxs-lookup"><span data-stu-id="a4ee3-240">To specify reporting options:</span></span>  
  
    1.  <span data-ttu-id="a4ee3-241">在設計空間的工具列中，按一下 **[報表與記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-241">In the design space's toolbar, click **Reporting and Logging**.</span></span>  
  
    2.  <span data-ttu-id="a4ee3-242">在 **[報表與記錄]** 對話方塊中的 **[報表]** 底下，選取 **[產生文字檔報表]** 、 **[傳送報表至電子郵件收件者]** 或兩者。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-242">In the **Reporting and Logging** dialog box, under **Reporting**, select **Generate a text file report** or **Send report to an email recipient** or both.</span></span>  
  
        1.  <span data-ttu-id="a4ee3-243">如果您選取 **[產生文字檔報表]** ，請選取 **[建立新檔案]** 或 **[附加至檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-243">If you select **Generate a text file report**, select either **Create a new file** or **Append to file**.</span></span>  
  
        2.  <span data-ttu-id="a4ee3-244">根據上述選項，透過在 **[資料夾]** 或 **[檔案名稱]** 方塊中輸入資訊，輸入新檔案或要附加之檔案的名稱和完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-244">Depending on the selection above, enter the name and full path of the new file or file to be appended by entering the information in the **Folder** or **File name** boxes.</span></span> <span data-ttu-id="a4ee3-245">或者，按一下省略號\*\* ( ... ) \*\* ，然後從 [**尋找資料夾-**_Server_name_ ] 或 [**尋找資料庫檔案-**_server_name_ ] 對話方塊中選取資料夾或檔案名的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-245">Alternately, click on the ellipsis **(...)** and select the path to the folder or file name from the **Locate Folder -**_server_name_ or **Locate Database Files -**_server_name_ dialog boxes.</span></span>  
  
        3.  <span data-ttu-id="a4ee3-246">如果您選取 **[傳送報表至電子郵件收件者]** ，請在 **[代理程式操作員]** 清單中選取電子郵件報表的收件者。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-246">If you select **Send report to an email recipient**, on the **Agent operator** list, select the recipient of the emailed report.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="a4ee3-247">SQL Server Agent 必須設定為使用 Database Mail，才能傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-247">SQL Server Agent must be configured to use Database Mail in order to send mail.</span></span> <span data-ttu-id="a4ee3-248">如需相關資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span><span class="sxs-lookup"><span data-stu-id="a4ee3-248">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span></span>  
  
    3.  <span data-ttu-id="a4ee3-249">若要儲存更詳細的資訊，請在 **[記錄]** 底下選取 **[記錄擴充資訊]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-249">To save more detailed information, under **Logging**, select **Log extended information**.</span></span>  
  
    4.  <span data-ttu-id="a4ee3-250">若要將維護計畫結果資訊寫入其他伺服器，請選取 **[記錄到遠端伺服器]** ，然後從 **[連接]** 清單中選取伺服器連接，或按一下 **[新增]** 並在 **[連接屬性]** 對話方塊中輸入連接資訊。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-250">To write maintenance plan results information to another server, select **Log to remote server** and either select a server connection from the **Connection** list or click **New** and enter the connection information in the **Connection Properties** dialog box.</span></span>  
  
    5.  <span data-ttu-id="a4ee3-251">在 **[報表與記錄]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-251">In the **Reporting and Logging** dialog box, click **OK**.</span></span>  
  
12. <span data-ttu-id="a4ee3-252">若要在記錄檔檢視器中檢視結果，請在物件總管中以滑鼠右鍵按一下 [維護計畫] 資料夾或特定維護計畫，然後選取 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-252">To view the results in the log file viewer, in **Object Explorer**, right-click either the **Maintenance Plans** folder or the specific maintenance plan and select **View History**.</span></span>  
  
     <span data-ttu-id="a4ee3-253">[**記錄檔檢視器-**_server_name_ ] 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-253">The following options are available on the **Log File Viewer -**_server_name_ dialog box.</span></span>  
  
     <span data-ttu-id="a4ee3-254">**載入記錄**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-254">**Load Log**</span></span>  
     <span data-ttu-id="a4ee3-255">開啟對話方塊供您指定所要載入的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-255">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="a4ee3-256">**匯出**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-256">**Export**</span></span>  
     <span data-ttu-id="a4ee3-257">開啟對話方塊，以讓您將 [記錄檔摘要] 格線中所顯示的資訊匯出至文字檔。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-257">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="a4ee3-258">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-258">**Refresh**</span></span>  
     <span data-ttu-id="a4ee3-259">重新整理所選取之記錄檔的檢視。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-259">Refresh the view of the selected logs.</span></span> <span data-ttu-id="a4ee3-260">當套用任何篩選設定時， **[重新整理]** 按鈕會從目標伺服器重新讀取選取的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-260">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="a4ee3-261">**Filter**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-261">**Filter**</span></span>  
     <span data-ttu-id="a4ee3-262">開啟對話方塊，以讓您指定用來篩選記錄檔的設定，例如 [連接]、[日期] 或其他的 [一般] 篩選準則。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-262">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="a4ee3-263">**搜尋**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-263">**Search**</span></span>  
     <span data-ttu-id="a4ee3-264">搜尋記錄檔中的特定文字。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-264">Search the log file for specific text.</span></span> <span data-ttu-id="a4ee3-265">不支援使用萬用字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-265">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="a4ee3-266">**停止**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-266">**Stop**</span></span>  
     <span data-ttu-id="a4ee3-267">停止載入記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-267">Stops loading the log file entries.</span></span> <span data-ttu-id="a4ee3-268">例如，如果遠端或離線記錄檔需要長時間才能載入，而您只要檢視最新項目時，就可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-268">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="a4ee3-269">**記錄檔摘要**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-269">**Log file summary**</span></span>  
     <span data-ttu-id="a4ee3-270">此資訊面板會顯示記錄檔篩選的摘要。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-270">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="a4ee3-271">如果未篩選檔案，則會看到下列文字： **[未套用篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-271">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="a4ee3-272">若篩選已套用到記錄，則會看到下列文字：**篩選記錄項目的準則：\<filter criteria>** 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-272">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="a4ee3-273">**日期**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-273">**Date**</span></span>  
     <span data-ttu-id="a4ee3-274">顯示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-274">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="a4ee3-275">**Source**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-275">**Source**</span></span>  
     <span data-ttu-id="a4ee3-276">顯示事件建立的來源功能，例如服務名稱 (如 MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-276">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="a4ee3-277">不是所有記錄檔類型都會出現來源。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-277">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="a4ee3-278">**訊息**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-278">**Message**</span></span>  
     <span data-ttu-id="a4ee3-279">顯示與事件相關聯的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-279">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="a4ee3-280">**記錄類型**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-280">**Log Type**</span></span>  
     <span data-ttu-id="a4ee3-281">顯示事件所屬之記錄檔的類型。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-281">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="a4ee3-282">所有選取的記錄檔都會出現在記錄檔摘要視窗中。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-282">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="a4ee3-283">**記錄來源**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-283">**Log Source**</span></span>  
     <span data-ttu-id="a4ee3-284">顯示擷取事件之來源記錄的描述。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-284">Displays a description of the source log in which the event is captured.</span></span>  
  
     <span data-ttu-id="a4ee3-285">**選取的資料列詳細資料**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-285">**Selected row details**</span></span>  
     <span data-ttu-id="a4ee3-286">選取資料列以顯示頁面下方有關選取之事件資料列的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-286">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="a4ee3-287">將資料行拖曳至方格中的新位置，以重新排序資料行。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-287">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="a4ee3-288">將方格標頭中的資料行分隔線拖曳至左邊或右邊，以調整資料行大小。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-288">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="a4ee3-289">在方格標頭中按兩下資料行分隔線，自動將資料行大小調整為內容寬度。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-289">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="a4ee3-290">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="a4ee3-290">**Instance**</span></span>  
     <span data-ttu-id="a4ee3-291">發生事件之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-291">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="a4ee3-292">顯示為 *&lt;電腦名稱*\\*執行個體名稱&gt;* 。</span><span class="sxs-lookup"><span data-stu-id="a4ee3-292">This is displayed as *computer name*\\*instance name*.</span></span>  
  
  
