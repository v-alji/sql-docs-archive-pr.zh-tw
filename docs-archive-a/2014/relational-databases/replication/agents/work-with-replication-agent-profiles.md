---
title: 處理複寫代理程式設定檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc20451edfb1096fca7e468effb14df78b51f758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585889"
---
# <a name="work-with-replication-agent-profiles"></a><span data-ttu-id="a6338-102">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-102">Work with Replication Agent Profiles</span></span>
  <span data-ttu-id="a6338-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中處理複寫代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-103">This topic describes how to work with Replication Agent Profiles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="a6338-104">每個複寫代理程式的行為由一組可在代理程式設定檔中設定的參數來控制。</span><span class="sxs-lookup"><span data-stu-id="a6338-104">The behavior of each replication agent is controlled by a set of parameters that can be set through agent profiles.</span></span> <span data-ttu-id="a6338-105">各代理程式都有預設的設定檔，某些代理程式還擁有其他預先定義的設定檔；在某一給定時刻，代理程式只使用一個設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-105">Each agent has a default profile, and some have additional predefined profiles; at a given time, only one profile is active for an agent.</span></span>  
  
 <span data-ttu-id="a6338-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a6338-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a6338-107">**若要處理複寫代理程式設定檔，請使用：**</span><span class="sxs-lookup"><span data-stu-id="a6338-107">**To work with Replication Agent Profiles, using:**</span></span>  
  
     [<span data-ttu-id="a6338-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6338-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   <span data-ttu-id="a6338-109">存取代理程式設定檔對話方塊</span><span class="sxs-lookup"><span data-stu-id="a6338-109">Access the Agent Profiles dialog box</span></span>  
  
    -   <span data-ttu-id="a6338-110">為代理程式指定設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-110">Specify a profile for an agent</span></span>  
  
    -   <span data-ttu-id="a6338-111">建立設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-111">Create a profile</span></span>  
  
    -   <span data-ttu-id="a6338-112">修改設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-112">Modify a profile</span></span>  
  
    -   <span data-ttu-id="a6338-113">刪除設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-113">Delete a profile</span></span>  
  
     [<span data-ttu-id="a6338-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6338-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   <span data-ttu-id="a6338-115">建立設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-115">Create a profile</span></span>  
  
    -   <span data-ttu-id="a6338-116">修改設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-116">Modify a profile</span></span>  
  
    -   <span data-ttu-id="a6338-117">刪除設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-117">Delete a profile</span></span>  
  
    -   <span data-ttu-id="a6338-118">在同步處理期間使用代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-118">Use agent profiles during synchronization</span></span>  
  
    -   <span data-ttu-id="a6338-119">Transact-SQL 範例</span><span class="sxs-lookup"><span data-stu-id="a6338-119">Transact-SQL example</span></span>  
  
     [<span data-ttu-id="a6338-120">Replication Management Objects</span><span class="sxs-lookup"><span data-stu-id="a6338-120">Replication Management Objects</span></span>](#RMOProcedure)  
  
    -   <span data-ttu-id="a6338-121">建立設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-121">Create a profile</span></span>  
  
    -   <span data-ttu-id="a6338-122">修改設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-122">Modify a profile</span></span>  
  
    -   <span data-ttu-id="a6338-123">刪除設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-123">Delete a profile</span></span>  
  
-   <span data-ttu-id="a6338-124">**後續操作：** [在變更代理程式參數之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a6338-124">**Follow Up:**  [After Changing Agent Parameters](#FollowUp)</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a6338-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6338-125">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> <span data-ttu-id="a6338-126">若要透過 SQL Server Management Studio 存取代理程式設定檔對話方塊</span><span class="sxs-lookup"><span data-stu-id="a6338-126">To access the Agent Profiles dialog box from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a6338-127">在 [散發者屬性 - \<Distributor>] 對話方塊的 [一般] 頁面上，按一下 [設定檔預設值]。</span><span class="sxs-lookup"><span data-stu-id="a6338-127">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click **Profile Defaults**.</span></span>  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a><span data-ttu-id="a6338-128">若要透過複寫監視器存取代理程式設定檔對話方塊</span><span class="sxs-lookup"><span data-stu-id="a6338-128">To access the Agent Profiles dialog box from Replication Monitor</span></span>  
  
-   <span data-ttu-id="a6338-129">若要開啟所有代理程式的對話方塊，請以滑鼠右鍵按一下「發行者」，然後按一下 **[代理程式設定檔]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-129">To open the dialog box for all agents, right-click a Publisher, and then click **Agent Profiles**.</span></span>  
  
-   <span data-ttu-id="a6338-130">若要開啟單一代理程式的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="a6338-130">To open the dialog box for a single agent:</span></span>  
  
    1.  <span data-ttu-id="a6338-131">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="a6338-131">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="a6338-132">對於「散發代理程式」和「合併代理程式」設定檔，請以滑鼠右鍵按一下 **[所有訂閱]** 索引標籤上的訂閱，然後按一下 **[代理程式設定檔]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-132">For Distribution Agent and Merge Agent profiles, right-click a subscription on the **All Subscriptions** tab, and then click **Agent Profile**.</span></span> <span data-ttu-id="a6338-133">對於其他代理程式，請以滑鼠右鍵按一下 **[代理程式]** 索引標籤，然後按一下 **[代理程式設定檔]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-133">For other agents, right-click the agent on the **Agents** tab, and then click **Agent Profile**.</span></span>  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> <span data-ttu-id="a6338-134">若要為代理程式指定設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-134">To specify a profile for an agent</span></span>  
  
1.  <span data-ttu-id="a6338-135">如果 **[代理程式設定檔]** 對話方塊顯示一個以上的代理程式設定檔，請選取一個代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-135">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="a6338-136">在 **[代理程式設定檔]** 方格的 **[新項目的預設值]** 資料行中選取一個設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-136">Select a profile in the **Default for new** column of the **Agent profiles** grid.</span></span> <span data-ttu-id="a6338-137">依預設，設定檔只會套用至新發行集和訂閱的代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-137">By default, the profile is only applied to agents for new publications and subscriptions.</span></span>  
  
3.  <span data-ttu-id="a6338-138">若要指定現有發行集或訂閱之選定類型的所有代理程式應使用此設定檔，請按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-138">To specify that all agents of the selected type for existing publications or subscriptions should use this profile, click **Change existing agents**.</span></span>  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> <span data-ttu-id="a6338-139">若要檢視和編輯設定檔的相關參數</span><span class="sxs-lookup"><span data-stu-id="a6338-139">To view and edit the parameters associated with a profile</span></span>  
  
1.  <span data-ttu-id="a6338-140">如果 **[代理程式設定檔]** 對話方塊顯示一個以上的代理程式設定檔，請選取一個代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-140">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="a6338-141">按一下設定檔旁邊的屬性按鈕 ([...])。</span><span class="sxs-lookup"><span data-stu-id="a6338-141">Click the properties button (**...**) next to a profile.</span></span>  
  
3.  <span data-ttu-id="a6338-142">檢視 [\<ProfileName> 設定檔屬性] 對話方塊中的參數和值。</span><span class="sxs-lookup"><span data-stu-id="a6338-142">View the parameters and values in the **\<ProfileName> Profile Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="a6338-143">可以編輯使用者自訂之設定檔中的參數；但無法編輯預先定義之系統設定檔中的參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-143">Parameters in user-defined profiles can be edited; parameters in predefined system profiles cannot.</span></span>  
  
    -   <span data-ttu-id="a6338-144">若要檢視代理程式的所有參數，請清除 **[只顯示這個設定檔中使用的參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a6338-144">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="a6338-145">如需有關代理程式參數的資訊，請參閱此主題結尾處的連結。</span><span class="sxs-lookup"><span data-stu-id="a6338-145">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
4.  <span data-ttu-id="a6338-146">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="a6338-146">Click **Close**.</span></span>  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> <span data-ttu-id="a6338-147">若要建立使用者自訂的設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-147">To create a user-defined profile</span></span>  
  
1.  <span data-ttu-id="a6338-148">如果 **[代理程式設定檔]** 對話方塊顯示一個以上的代理程式設定檔，請選取一個代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-148">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="a6338-149">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-149">Click **New**.</span></span>  
  
3.  <span data-ttu-id="a6338-150">在 **[新增代理程式設定檔]** 初始化對話方塊中，選取新設定檔所依據的現有設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-150">In the **New Agent Profile** initialization dialog box, select an existing profile on which to base the new profile.</span></span>  
  
4.  <span data-ttu-id="a6338-151">在 **[新增代理程式設定檔]** 對話方塊中，於 **[名稱]** 和 **[說明]** 文字方塊內輸入值。</span><span class="sxs-lookup"><span data-stu-id="a6338-151">In the **New Agent Profile** dialog box, enter values in the **Name** and **Description** text boxes.</span></span>  
  
5.  <span data-ttu-id="a6338-152">修改參數以使其適用於設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-152">Modify parameters to tailor the profile.</span></span> <span data-ttu-id="a6338-153">若要檢視代理程式的所有參數，請清除 **[只顯示這個設定檔中使用的參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a6338-153">To view all parameters for an agent, clear the **Show only parameters used in this profile** check box.</span></span> <span data-ttu-id="a6338-154">如需有關代理程式參數的資訊，請參閱此主題結尾處的連結。</span><span class="sxs-lookup"><span data-stu-id="a6338-154">For information about agent parameters, see the links at the end of this topic.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> <span data-ttu-id="a6338-155">若要刪除使用者自訂的設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-155">To delete a user-defined profile</span></span>  
  
1.  <span data-ttu-id="a6338-156">如果 **[代理程式設定檔]** 對話方塊顯示一個以上的代理程式設定檔，請選取一個代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-156">If the **Agent Profiles** dialog box displays profiles for more than one agent, select an agent.</span></span>  
  
2.  <span data-ttu-id="a6338-157">如果設定檔與一個或多個代理程式相關聯，請變更這些代理程式的設定檔：</span><span class="sxs-lookup"><span data-stu-id="a6338-157">If a profile is associated with one or more agents, change the profile for those agents:</span></span>  
  
    1.  <span data-ttu-id="a6338-158">請在 **[代理程式設定檔]** 方格中選取其他設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-158">Select a different profile in the **Agent profiles** grid.</span></span>  
  
    2.  <span data-ttu-id="a6338-159">按一下 **[變更現有的代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-159">Click **Change existing agents**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a6338-160">這將變更現有發行集或訂閱之所有選定類型代理程式的設定檔，而不僅僅是使用您要刪除之設定檔的代理程式。</span><span class="sxs-lookup"><span data-stu-id="a6338-160">This will change the profile for all agents of the selected type for existing publications or subscriptions, not only the ones using the profile you want to delete.</span></span>  
  
3.  <span data-ttu-id="a6338-161">選取您要刪除的設定檔，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-161">Select the profile you want to delete, and then click **Delete**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a6338-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6338-162">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> <span data-ttu-id="a6338-163">若要建立新的代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-163">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-164">在散發者端，執行 [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-164">At the Distributor, execute [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-165">指定 **@name** 、 **1**的值 **@profile_type** ，以及下列其中一個值 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="a6338-165">Specify **@name**, a value of **1** for **@profile_type**, and one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="a6338-166">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-166">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-167">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-168">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-169">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-170">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="a6338-171">如果此設定檔將成為其複寫代理程式類型的新預設設定檔，請針對 **@profile_type** 指定 **@default**。</span><span class="sxs-lookup"><span data-stu-id="a6338-171">If this profile will become the new default profile for its type of replication agent, specify a value of **1** for **@default**.</span></span> <span data-ttu-id="a6338-172">新設定檔的識別碼會使用 **@profile_id** 輸出參數傳回。</span><span class="sxs-lookup"><span data-stu-id="a6338-172">The identifier for the new profile is returned using the **@profile_id** output parameter.</span></span> <span data-ttu-id="a6338-173">如此會根據給定的代理程式類型，建立具有一組設定檔參數的新設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-173">This creates a new profile with a set of profile parameters based on the default profile for the given agent type.</span></span>  
  
2.  <span data-ttu-id="a6338-174">在建立新設定檔之後，可以加入、移除或修改預設的參數來自訂該設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-174">After the new profile has been created, add, remove, or modify the default parameters to customize the profile.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> <span data-ttu-id="a6338-175">若要修改現有的代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-175">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-176">在散發者端，執行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-176">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-177">針對指定下列其中一個值 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="a6338-177">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="a6338-178">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-178">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-179">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-180">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-181">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-182">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="a6338-183">這會傳回指定的代理程式類型的所有設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-183">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="a6338-184">請注意結果集中要變更之設定檔的 **profile_id** 值。</span><span class="sxs-lookup"><span data-stu-id="a6338-184">Note the value of **profile_id** in the result set for the profile to change.</span></span>  
  
2.  <span data-ttu-id="a6338-185">在散發者端，執行 [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-185">At the Distributor, execute [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql).</span></span> <span data-ttu-id="a6338-186">針對指定步驟1中的設定檔識別碼 **@profile_id** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-186">Specify the profile identifier from step 1 for **@profile_id**.</span></span> <span data-ttu-id="a6338-187">這會傳回設定檔的所有參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-187">This returns all parameters for the profile.</span></span> <span data-ttu-id="a6338-188">請注意要在設定檔中修改或移除的任何參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-188">Note the name of any parameters to modify or remove from the profile.</span></span>  
  
3.  <span data-ttu-id="a6338-189">若要變更設定檔中的參數值，請執行 [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-189">To change the value of a parameter in a profile, execute [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-190">針對指定步驟1中的設定檔識別碼 **@profile_id** 、針對變更的參數名稱，並為的 **@property** 參數指定新的值 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-190">Specify the profile identifier from step 1 for **@profile_id**, the name of the parameter to change for **@property**, and a new value for the parameter for **@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6338-191">您無法變更現有的代理程式設定檔，使其成為代理程式的預設設定檔，</span><span class="sxs-lookup"><span data-stu-id="a6338-191">You cannot change an existing agent profile to become the default profile for an agent.</span></span> <span data-ttu-id="a6338-192">而必須建立新的預設檔當做預設設定檔，如前述程序所示。</span><span class="sxs-lookup"><span data-stu-id="a6338-192">You must instead create a new profile as the default profile, as shown in the previous procedure.</span></span>  
  
4.  <span data-ttu-id="a6338-193">若要從設定檔移除參數，請執行 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-193">To remove a parameter from a profile, execute [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql).</span></span> <span data-ttu-id="a6338-194">針對指定步驟1中的設定檔識別碼 **@profile_id** ，並針對要移除之參數的 **@parameter_name** 名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-194">Specify the profile identifier from step 1 for **@profile_id** and the name of the parameter to remove for **@parameter_name**.</span></span>  
  
5.  <span data-ttu-id="a6338-195">若要在設定檔中加入新參數，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a6338-195">To add a new parameter to a profile, you must do the following:</span></span>  
  
    -   <span data-ttu-id="a6338-196">查詢「散發者」端的 [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) 資料表，以判斷可針對每個代理程式類型所設定的設定檔參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-196">Query the [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) table at the Distributor to determine which profile parameters can be set for each agent type.</span></span>  
  
    -   <span data-ttu-id="a6338-197">在散發者端，執行 [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-197">At the Distributor, execute [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql).</span></span> <span data-ttu-id="a6338-198">針對指定步驟1中的設定檔識別碼 **@profile_id** 、針對新增的有效參數名稱， **@parameter_name** 以及的參數值 **@parameter_value** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-198">Specify the profile identifier from step 1 for **@profile_id**, the name of a valid parameter to add for **@parameter_name**, and the value of the parameter for **@parameter_value**.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> <span data-ttu-id="a6338-199">若要刪除代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-199">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-200">在散發者端，執行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-200">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-201">針對指定下列其中一個值 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="a6338-201">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="a6338-202">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-202">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-203">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-204">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-205">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-206">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="a6338-207">這會傳回指定的代理程式類型的所有設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-207">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="a6338-208">請注意結果集中要移除之設定檔的 **profile_id** 值。</span><span class="sxs-lookup"><span data-stu-id="a6338-208">Note the value of **profile_id** in the result set for the profile to remove.</span></span>  
  
2.  <span data-ttu-id="a6338-209">在散發者端，執行 [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-209">At the Distributor, execute [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-210">針對指定步驟1中的設定檔識別碼 **@profile_id** 。</span><span class="sxs-lookup"><span data-stu-id="a6338-210">Specify the profile identifier from step 1 for **@profile_id**.</span></span>  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> <span data-ttu-id="a6338-211">若要在同步處理期間使用代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-211">To use agent profiles during synchronization</span></span>  
  
1.  <span data-ttu-id="a6338-212">在散發者端，執行 [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6338-212">At the Distributor, execute [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql).</span></span> <span data-ttu-id="a6338-213">針對指定下列其中一個值 **@agent_type** ：</span><span class="sxs-lookup"><span data-stu-id="a6338-213">Specify one of the following values for **@agent_type**:</span></span>  
  
    -   <span data-ttu-id="a6338-214">**\@profile_type** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-214">**1** - [Replication Snapshot Agent](replication-snapshot-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-215">**2** - [Replication Log Reader Agent](replication-log-reader-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-216">**3** - [Replication Distribution Agent](replication-distribution-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-217">**4** - [Replication Merge Agent](replication-merge-agent.md)</span></span>  
  
    -   <span data-ttu-id="a6338-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span><span class="sxs-lookup"><span data-stu-id="a6338-218">**9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)</span></span>  
  
     <span data-ttu-id="a6338-219">這會傳回指定的代理程式類型的所有設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-219">This returns all profiles for the specified type of agent.</span></span> <span data-ttu-id="a6338-220">請注意 `profile_name` 結果集中要使用之設定檔的值。</span><span class="sxs-lookup"><span data-stu-id="a6338-220">Note the value of `profile_name` in the result set for the profile to use.</span></span>  
  
2.  <span data-ttu-id="a6338-221">如果代理程式是從代理程式作業啟動的，請編輯啟動代理程式的作業步驟， `profile_name` 在 **-ProfileName**命令列參數之後指定在步驟1中取得的值。</span><span class="sxs-lookup"><span data-stu-id="a6338-221">If the agent is started from an agent job, edit the job step that starts the agent to specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span> <span data-ttu-id="a6338-222">如需詳細資訊，請參閱[檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a6338-222">For more information, see [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).</span></span>  
  
3.  <span data-ttu-id="a6338-223">從命令提示字元啟動代理程式時，請 `profile_name` 在 **-ProfileName**命令列參數之後指定在步驟1中取得的值。</span><span class="sxs-lookup"><span data-stu-id="a6338-223">When starting the agent from the command prompt, specify the value of `profile_name` obtained in step 1 after the **-ProfileName** command-line parameter.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a6338-224">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a6338-224">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="a6338-225">此範例會針對名為 **custom_merge**的合併代理程式建立自訂的設定檔、變更 **-UploadReadChangesPerBatch** 參數的值、加入新的 **-ExchangeType** 參數，並傳回所建立之設定檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a6338-225">This example creates a custom profile for the Merge Agent named **custom_merge**, changes the value of the **-UploadReadChangesPerBatch** parameter, adds a new **-ExchangeType** parameter, and returns information on the profile that is created.</span></span>  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="a6338-226">使用 RMO</span><span class="sxs-lookup"><span data-stu-id="a6338-226">Using RMO</span></span>  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> <span data-ttu-id="a6338-227">若要建立新的代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-227">To create a new agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-228">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別的執行個體建立與「散發者」的連接。</span><span class="sxs-lookup"><span data-stu-id="a6338-228">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a6338-229">建立 <xref:Microsoft.SqlServer.Replication.AgentProfile> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6338-229">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span>  
  
3.  <span data-ttu-id="a6338-230">設定物件的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a6338-230">Set the following properties on the object:</span></span>  
  
    -   <span data-ttu-id="a6338-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - 設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-231"><xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - the name for the profile.</span></span>  
  
    -   <span data-ttu-id="a6338-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - <xref:Microsoft.SqlServer.Replication.AgentType> 值，指定為其建立設定檔的複寫代理程式類型。</span><span class="sxs-lookup"><span data-stu-id="a6338-232"><xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - an <xref:Microsoft.SqlServer.Replication.AgentType> value that specifies the type of replication agent for which the profile is being created.</span></span>  
  
    -   <span data-ttu-id="a6338-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - 在步驟 1 中建立的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="a6338-233"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
    -   <span data-ttu-id="a6338-234">(選擇性) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - 設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="a6338-234">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - a description of the profile.</span></span>  
  
    -   <span data-ttu-id="a6338-235">(選擇性) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - 如果依預設這個 <xref:Microsoft.SqlServer.Replication.AgentType> 的所有新代理程式作業都會使用這個設定檔，請將此屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6338-235">(Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - set this property to `true` if all new agent jobs for this <xref:Microsoft.SqlServer.Replication.AgentType> will use this profile by default.</span></span>  
  
4.  <span data-ttu-id="a6338-236">呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> 方法，以在伺服器上建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-236">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> method to create the profile on the server.</span></span>  
  
5.  <span data-ttu-id="a6338-237">在伺服器上建立設定檔之後，就可以藉由加入、移除或變更複寫代理程式參數的值來加以自訂。</span><span class="sxs-lookup"><span data-stu-id="a6338-237">Once the profile exists on the server, you can customize it by adding, removing, or changing the values of replication agent parameters.</span></span>  
  
6.  <span data-ttu-id="a6338-238">若要將設定檔指派給現有的複寫代理程式作業，請呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-238">To assign the profile to an existing replication agent job, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> method.</span></span> <span data-ttu-id="a6338-239">請針對 *distributionDBName* 傳遞散發資料庫的名稱，而針對 *agentID*傳遞作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6338-239">Pass the name of the distribution database for *distributionDBName* and the ID of the job for *agentID*.</span></span>  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> <span data-ttu-id="a6338-240">若要修改現有的代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-240">To modify an existing agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-241">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別的執行個體建立與「散發者」的連接。</span><span class="sxs-lookup"><span data-stu-id="a6338-241">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a6338-242">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6338-242">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="a6338-243">傳遞在步驟 1 中建立的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="a6338-243">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object created in step 1.</span></span>  
  
3.  <span data-ttu-id="a6338-244">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-244">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="a6338-245">如果此方法傳回 `false`，請確認「散發者」存在。</span><span class="sxs-lookup"><span data-stu-id="a6338-245">If this method returns `false`, verify that the Distributor exists.</span></span>  
  
4.  <span data-ttu-id="a6338-246">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-246">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> method.</span></span> <span data-ttu-id="a6338-247">傳遞 <xref:Microsoft.SqlServer.Replication.AgentType> 值，將傳回的設定檔縮減為特定的複寫代理程式類型。</span><span class="sxs-lookup"><span data-stu-id="a6338-247">Pass an <xref:Microsoft.SqlServer.Replication.AgentType> value to narrow down the returned profiles to a specific type of replication agent.</span></span>  
  
5.  <span data-ttu-id="a6338-248">從傳回的 <xref:Microsoft.SqlServer.Replication.AgentProfile> 取得想要的 <xref:System.Collections.ArrayList>物件，其中物件的 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> 屬性符合設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-248">Get the desired <xref:Microsoft.SqlServer.Replication.AgentProfile> object from the returned <xref:System.Collections.ArrayList>, where the <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> property of the object matches the profile name.</span></span>  
  
6.  <span data-ttu-id="a6338-249">呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile> 的下列其中一個方法來變更設定檔：</span><span class="sxs-lookup"><span data-stu-id="a6338-249">Call one of the following methods of <xref:Microsoft.SqlServer.Replication.AgentProfile> to change the profile:</span></span>  
  
    -   <span data-ttu-id="a6338-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - 將支援的參數加入至設定檔，其中 *name* 是複寫代理程式參數的名稱， *value* 則是指定的值。</span><span class="sxs-lookup"><span data-stu-id="a6338-250"><xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - adds a supported parameter to the profile, where *name* is the name of the replication agent parameter and *value* is the specified value.</span></span> <span data-ttu-id="a6338-251">若要列舉給定代理程式類型的所有受支援的代理程式參數，請呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-251">To enumerate all supported agent parameters for a given agent type, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="a6338-252">這個方法會傳回 <xref:System.Collections.ArrayList> 物件的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> ，代表所有受支援的參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-252">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent all supported parameters.</span></span>  
  
    -   <span data-ttu-id="a6338-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - 從設定檔移除現有的參數，其中 *name* 是複寫代理程式參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-253"><xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - removes an existing parameter from the profile, where *name* is the name of the replication agent parameter.</span></span> <span data-ttu-id="a6338-254">若要列舉所有目前為設定檔所定義的代理程式參數，請呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-254">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="a6338-255">這個方法會傳回 <xref:System.Collections.ArrayList> 物件的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> ，代表此設定檔的現有參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-255">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span>  
  
    -   <span data-ttu-id="a6338-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - 變更設定檔中現有參數的設定，其中 *name* 是代理程式參數的名稱，而 *newValue* 則是參數要變更成的值。</span><span class="sxs-lookup"><span data-stu-id="a6338-256"><xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - changes the setting of an existing parameter in the profile, where *name* is the name of the agent parameter and *newValue* is the value to which the parameter is being changed.</span></span> <span data-ttu-id="a6338-257">若要列舉所有目前為設定檔所定義的代理程式參數，請呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-257">To enumerate all current agent parameters defined for the profile, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> method.</span></span> <span data-ttu-id="a6338-258">這個方法會傳回 <xref:System.Collections.ArrayList> 物件的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> ，代表此設定檔的現有參數。</span><span class="sxs-lookup"><span data-stu-id="a6338-258">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objects that represent the existing parameter for this profile.</span></span> <span data-ttu-id="a6338-259">若要列舉所有受支援的代理程式參數設定，請呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-259">To enumerate all supported agent parameter settings, call the <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> method.</span></span> <span data-ttu-id="a6338-260">這個方法會傳回 <xref:System.Collections.ArrayList> 物件的 <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> ，代表所有受支援的參數值。</span><span class="sxs-lookup"><span data-stu-id="a6338-260">This method returns an <xref:System.Collections.ArrayList> of <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> objects that represent the supported values for all parameters.</span></span>  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> <span data-ttu-id="a6338-261">若要刪除代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="a6338-261">To delete an agent profile</span></span>  
  
1.  <span data-ttu-id="a6338-262">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別的執行個體建立與「散發者」的連接。</span><span class="sxs-lookup"><span data-stu-id="a6338-262">Create a connection to the Distributor by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="a6338-263">建立 <xref:Microsoft.SqlServer.Replication.AgentProfile> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6338-263">Create an instance of the <xref:Microsoft.SqlServer.Replication.AgentProfile> class.</span></span> <span data-ttu-id="a6338-264">針對 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> ，設定步驟 1 的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 和 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>的設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="a6338-264">Set the name of the profile for <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="a6338-265">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6338-265">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="a6338-266">如果此方法傳回 `false`，則指定的名稱不正確，或伺服器上不存在該設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-266">If this method returns `false`, either the specified name was incorrect or the profile does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="a6338-267">確認 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> 屬性是設定為 <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>，這代表客戶的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-267">Verify that the <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> property is set to <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, which indicates a customer profile.</span></span> <span data-ttu-id="a6338-268">您不該移除 <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> 的值為 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>的設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-268">You should not remove a profile that has a value of <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> for <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.</span></span>  
  
5.  <span data-ttu-id="a6338-269">呼叫 <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> 方法，從伺服器移除此物件代表的使用者自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="a6338-269">Call the <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> method to remove the user-defined profile represented by this object from the server.</span></span>  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a> <span data-ttu-id="a6338-270">後續操作：在變更代理程式參數之後</span><span class="sxs-lookup"><span data-stu-id="a6338-270">Follow Up: After Changing Agent Parameters</span></span>  
 <span data-ttu-id="a6338-271">代理程式參數變更會在代理程式下次啟動時生效。</span><span class="sxs-lookup"><span data-stu-id="a6338-271">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="a6338-272">如果代理程式連續執行，則必須停止代理程式，然後重新啟動它。</span><span class="sxs-lookup"><span data-stu-id="a6338-272">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6338-273">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6338-273">See Also</span></span>  
 <span data-ttu-id="a6338-274">[複寫代理程式設定檔](replication-agent-profiles.md) </span><span class="sxs-lookup"><span data-stu-id="a6338-274">[Replication Agent Profiles](replication-agent-profiles.md) </span></span>  
 <span data-ttu-id="a6338-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a6338-275">[Replication Snapshot Agent](replication-snapshot-agent.md) </span></span>  
 <span data-ttu-id="a6338-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a6338-276">[Replication Log Reader Agent](replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="a6338-277">[Replication Distribution Agent](replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a6338-277">[Replication Distribution Agent](replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="a6338-278">[Replication Merge Agent](replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a6338-278">[Replication Merge Agent](replication-merge-agent.md) </span></span>  
 [<span data-ttu-id="a6338-279">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="a6338-279">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)  
  
  
