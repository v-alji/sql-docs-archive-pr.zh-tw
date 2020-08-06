---
title: 設定原始檔控制選項 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d4ca19180a7291763780f300172bb2292a98c8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585570"
---
# <a name="set-source-control-options"></a><span data-ttu-id="57b72-102">設定原始檔控制選項</span><span class="sxs-lookup"><span data-stu-id="57b72-102">Set Source Control Options</span></span>
  <span data-ttu-id="57b72-103">在利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中所建立的原始檔控制功能之前，您應該先設定您的各種工作環境的原始檔控制選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-103">Before you take advantage of the source control features built into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you should configure your source control options for the various environments in which you work.</span></span>  
  
 <span data-ttu-id="57b72-104">您可以使用 [**選項**] 對話方塊來設定一個或多個原始檔控制角色，以設定原始檔控制選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-104">You configure source control options by using the **Options** dialog box to configure one or more source control roles.</span></span> <span data-ttu-id="57b72-105">角色由您在其中使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 之設定的一般描述，以及這項設定的相關原始檔控制選項所組成。</span><span class="sxs-lookup"><span data-stu-id="57b72-105">A role consists of a general description of the setting in which you use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and the source control options associated with that setting.</span></span>  
  
 <span data-ttu-id="57b72-106">例如，如果您是獨立的資料庫開發人員，則簽入檔案之後，通常會保留簽出的檔案，以避免與其他使用者發生衝突。</span><span class="sxs-lookup"><span data-stu-id="57b72-106">For example, if you are an independent database developer, you generally do not create conflicts with other users by keeping files checked out after you check them in.</span></span> <span data-ttu-id="57b72-107">因此，[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 會定義一個「獨立開發人員」角色。</span><span class="sxs-lookup"><span data-stu-id="57b72-107">Consequently, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] defines an Independent Developer role.</span></span> <span data-ttu-id="57b72-108">針對此角色， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 會自動選取 [**簽入時讓專案保持簽出**] 選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-108">For this role, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] automatically selects the **Keep items checked out when checking in** option.</span></span>  
  
 <span data-ttu-id="57b72-109">由於您可以定義和自訂角色，因此，您可以使用各種開發設定來工作，且不需要在每次切換不同設定時，全面重新設定原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="57b72-109">Because you can define and customize roles, you can work in varying development settings without having to completely reconfigure source control every time you move from one setting to another.</span></span>  
  
### <a name="to-set-source-control-options"></a><span data-ttu-id="57b72-110">設定原始檔控制選項</span><span class="sxs-lookup"><span data-stu-id="57b72-110">To set source control options</span></span>  
  
1.  <span data-ttu-id="57b72-111">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="57b72-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="57b72-112">在 [**選項**] 對話方塊中，展開 [**原始檔控制**]，然後按一下 [**外掛程式選取範圍]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="57b72-112">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
     <span data-ttu-id="57b72-113">**目前的原始檔控制外掛程式**</span><span class="sxs-lookup"><span data-stu-id="57b72-113">**Current source control plug-in**</span></span>  
     <span data-ttu-id="57b72-114">從此清單中選取您要使用的原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="57b72-114">Select the source control you want to use from this list.</span></span> <span data-ttu-id="57b72-115">原始檔控制產品用戶端必須安裝在此電腦上，才會顯示在清單中。</span><span class="sxs-lookup"><span data-stu-id="57b72-115">The source control product client must be installed on this computer to appear on the list.</span></span> <span data-ttu-id="57b72-116">如果電腦上未安裝原始檔控制用戶端，則唯一可用的選項將是「無」。</span><span class="sxs-lookup"><span data-stu-id="57b72-116">If no source control clients are installed on the computer, the only selection available will be None.</span></span> <span data-ttu-id="57b72-117">如果您已經安裝了 Microsoft Source Safe，則會顯示下列外掛程式：</span><span class="sxs-lookup"><span data-stu-id="57b72-117">If you have installed Microsoft Source Safe, then the following plug ins are displayed:</span></span>  
  
    -   <span data-ttu-id="57b72-118">Microsoft Visual SourceSafe</span><span class="sxs-lookup"><span data-stu-id="57b72-118">Microsoft Visual SourceSafe</span></span>  
  
    -   <span data-ttu-id="57b72-119">Microsoft Visual SourceSafe (網際網路)</span><span class="sxs-lookup"><span data-stu-id="57b72-119">Microsoft Visual SourceSafe(Internet)</span></span>  
  
3.  <span data-ttu-id="57b72-120">針對您要使用的每個原始檔控制角色設定登入認證。</span><span class="sxs-lookup"><span data-stu-id="57b72-120">Set login credentials for each source control role that you want to use.</span></span> <span data-ttu-id="57b72-121">只有安裝了原始檔控制外掛程式之後，才可以使用此頁面。</span><span class="sxs-lookup"><span data-stu-id="57b72-121">This page is only available if a source control plug-in is installed.</span></span>  
  
     <span data-ttu-id="57b72-122">**角色描述**</span><span class="sxs-lookup"><span data-stu-id="57b72-122">**Role Description**</span></span>  
     <span data-ttu-id="57b72-123">選取這些角色的其中之一，會自動選取適當的原始檔控制選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-123">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
    |<span data-ttu-id="57b72-124">角色</span><span class="sxs-lookup"><span data-stu-id="57b72-124">Role</span></span>|<span data-ttu-id="57b72-125">描述</span><span class="sxs-lookup"><span data-stu-id="57b72-125">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="57b72-126">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="57b72-126">**Visual SourceSafe**</span></span>|<span data-ttu-id="57b72-127">指定您想要使用 Visual SourceSafe 使用者最常使用的設定 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b72-127">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="57b72-128">**獨立開發人員**</span><span class="sxs-lookup"><span data-stu-id="57b72-128">**Independent Developer**</span></span>|<span data-ttu-id="57b72-129">指定您是獨立工作者。</span><span class="sxs-lookup"><span data-stu-id="57b72-129">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="57b72-130">**Custom**</span><span class="sxs-lookup"><span data-stu-id="57b72-130">**Custom**</span></span>|<span data-ttu-id="57b72-131">指定您已修改角色的設定。</span><span class="sxs-lookup"><span data-stu-id="57b72-131">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="57b72-132">**執行背景狀態更新**</span><span class="sxs-lookup"><span data-stu-id="57b72-132">**Perform background status updates**</span></span>  
     <span data-ttu-id="57b72-133">項目狀態變更時，會自動更新方案總管中的原始檔控制訊號圖示。</span><span class="sxs-lookup"><span data-stu-id="57b72-133">Automatically updates the source control signal icons in Solution Explorer as an item's status changes.</span></span> <span data-ttu-id="57b72-134">如果您在執行需要大量伺服器的作業時遭遇延遲，尤其是從原始檔控制開啟方案或專案時，清除此核取方塊就可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="57b72-134">If you experience delays when performing server-intensive operations, especially when opening a solution or project from source control, clearing this check box could improve performance.</span></span>  
  
     <span data-ttu-id="57b72-135">**登入識別碼**</span><span class="sxs-lookup"><span data-stu-id="57b72-135">**Login ID**</span></span>  
     <span data-ttu-id="57b72-136">指定用來登入原始檔控制提供者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="57b72-136">Specifies the user name to use to log in to the source control provider.</span></span> <span data-ttu-id="57b72-137">如果您的原始檔控制提供者支援，這個名稱將會自動填入 [**登**入] 對話方塊中，以連接到您的原始檔控制伺服器。</span><span class="sxs-lookup"><span data-stu-id="57b72-137">If supported by your source control provider, this name will be filled in automatically in the **Login** dialog box to reach your source control server.</span></span> <span data-ttu-id="57b72-138">若要讓這個選項成為使用中，請使用原始檔控制提供者的管理員程式，來停用自動使用者登入，然後重新啟動 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="57b72-138">To make this option active, disable automatic user logins by using your source control provider's administrator program, and then restart [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="57b72-139">**進階**</span><span class="sxs-lookup"><span data-stu-id="57b72-139">**Advanced**</span></span>  
     <span data-ttu-id="57b72-140">顯示將項目加入原始檔控制的其他選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-140">Displays additional options for adding items to source control.</span></span> <span data-ttu-id="57b72-141">這些選項會視原始檔控制提供者而不同。</span><span class="sxs-lookup"><span data-stu-id="57b72-141">These options vary depending on your source control provider.</span></span> <span data-ttu-id="57b72-142">這些選項的說明是由原始檔控制程式所提供。</span><span class="sxs-lookup"><span data-stu-id="57b72-142">Help for these options is provided by the source control program.</span></span>  
  
4.  <span data-ttu-id="57b72-143">選取 [**環境**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="57b72-143">Select the **Environment** page.</span></span>  
  
5.  <span data-ttu-id="57b72-144">在 [**原始檔控制環境設定**] 方塊中，選取您要設定原始檔控制選項的角色。</span><span class="sxs-lookup"><span data-stu-id="57b72-144">In the **Source Control Environment Settings** box, select the role on which you want to set source control options.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="57b72-145">會自動選取所選角色的預設原始檔控制選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-145">automatically selects the default source control options for the role you have selected.</span></span> <span data-ttu-id="57b72-146">如果您清除任何預設選項，[原始檔**控制環境設定**] 方塊會顯示 [**自訂**] 選項，指出您已自訂原先選取的角色。</span><span class="sxs-lookup"><span data-stu-id="57b72-146">If you clear any of the default options, the **Source Control Environment Settings** box displays the **Custom** option to indicate that you have customized the originally selected role.</span></span>  
  
     <span data-ttu-id="57b72-147">**原始檔控制環境設定**</span><span class="sxs-lookup"><span data-stu-id="57b72-147">**Source Control Environment Settings**</span></span>  
     <span data-ttu-id="57b72-148">指定您要使用的角色。</span><span class="sxs-lookup"><span data-stu-id="57b72-148">Specifies the role that you want to use.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="57b72-149">會定義下列角色。</span><span class="sxs-lookup"><span data-stu-id="57b72-149">defines the following roles.</span></span>  
  
    |<span data-ttu-id="57b72-150">角色</span><span class="sxs-lookup"><span data-stu-id="57b72-150">Role</span></span>|<span data-ttu-id="57b72-151">描述</span><span class="sxs-lookup"><span data-stu-id="57b72-151">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="57b72-152">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="57b72-152">**Visual SourceSafe**</span></span>|<span data-ttu-id="57b72-153">指定您想要使用 Visual SourceSafe 使用者最常使用的設定 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b72-153">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="57b72-154">**獨立開發人員**</span><span class="sxs-lookup"><span data-stu-id="57b72-154">**Independent Developer**</span></span>|<span data-ttu-id="57b72-155">指定您是獨立工作者。</span><span class="sxs-lookup"><span data-stu-id="57b72-155">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="57b72-156">**Custom**</span><span class="sxs-lookup"><span data-stu-id="57b72-156">**Custom**</span></span>|<span data-ttu-id="57b72-157">指定您已修改角色的設定。</span><span class="sxs-lookup"><span data-stu-id="57b72-157">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="57b72-158">選取這些角色的其中之一，會自動選取適當的原始檔控制選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-158">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
     <span data-ttu-id="57b72-159">**簽入時保持項目為簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-159">**Keep items checked out when checking in**</span></span>  
     <span data-ttu-id="57b72-160">指定當您簽入項目以更新原始檔控制存放區時，項目應保持簽出。</span><span class="sxs-lookup"><span data-stu-id="57b72-160">Specifies that when you check in items to update the source control store, the items should remain checked out to you.</span></span> <span data-ttu-id="57b72-161">如果您想要針對特定簽入變更此選項，請按一下 [**簽入**] 對話方塊中的 [**選項**] 箭號，然後清除 [**保持簽出**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-161">If you want to change this option for a specific check-in, click the **Options** arrow in the **Check in** dialog box, and then clear the **Keep checked out** check box.</span></span>  
  
     <span data-ttu-id="57b72-162">**已簽入的項目**</span><span class="sxs-lookup"><span data-stu-id="57b72-162">**Checked-in items**</span></span>  
     <span data-ttu-id="57b72-163">顯示選項清單，指定 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 當您嘗試編輯未簽出的專案時，應該如何表現。下表描述可用的選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-163">Displays a list of options that specify how [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] should behave when you attempt to edit an item that is not checked out. The following tables describe the available options.</span></span>  
  
     <span data-ttu-id="57b72-164">**儲存**</span><span class="sxs-lookup"><span data-stu-id="57b72-164">**Saving**</span></span>  
  
    |<span data-ttu-id="57b72-165">動作</span><span class="sxs-lookup"><span data-stu-id="57b72-165">Action</span></span>|<span data-ttu-id="57b72-166">描述</span><span class="sxs-lookup"><span data-stu-id="57b72-166">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="57b72-167">**提示簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-167">**Prompt for check out**</span></span>|<span data-ttu-id="57b72-168">顯示 [**簽出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-168">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="57b72-169">**自動簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-169">**Check out automatically**</span></span>|<span data-ttu-id="57b72-170">簽出項目，而不顯示 [**簽出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-170">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="57b72-171">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-171">This is the default option.</span></span>|  
    |<span data-ttu-id="57b72-172">**另存新檔**</span><span class="sxs-lookup"><span data-stu-id="57b72-172">**Save as**</span></span>|<span data-ttu-id="57b72-173">另存為新的檔案。</span><span class="sxs-lookup"><span data-stu-id="57b72-173">Saves as a new file.</span></span>|  
  
     <span data-ttu-id="57b72-174">**編輯中**</span><span class="sxs-lookup"><span data-stu-id="57b72-174">**Editing**</span></span>  
  
    |<span data-ttu-id="57b72-175">動作</span><span class="sxs-lookup"><span data-stu-id="57b72-175">Action</span></span>|<span data-ttu-id="57b72-176">描述</span><span class="sxs-lookup"><span data-stu-id="57b72-176">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="57b72-177">**提示簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-177">**Prompt for check out**</span></span>|<span data-ttu-id="57b72-178">顯示 [**簽出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-178">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="57b72-179">**提示獨佔簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-179">**Prompt for exclusive checkouts**</span></span>|<span data-ttu-id="57b72-180">顯示 [**簽出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-180">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="57b72-181">**自動簽出**</span><span class="sxs-lookup"><span data-stu-id="57b72-181">**Check out automatically**</span></span>|<span data-ttu-id="57b72-182">簽出項目，而不顯示 [**簽出**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57b72-182">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="57b72-183">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="57b72-183">This is the default option.</span></span>|  
    |<span data-ttu-id="57b72-184">**不執行任何動作**</span><span class="sxs-lookup"><span data-stu-id="57b72-184">**Do nothing**</span></span>|<span data-ttu-id="57b72-185">不要將檔案簽出。</span><span class="sxs-lookup"><span data-stu-id="57b72-185">Does not check out the file.</span></span>|  
  
     <span data-ttu-id="57b72-186">**允許編輯已簽入的項目**</span><span class="sxs-lookup"><span data-stu-id="57b72-186">**Allow checked-in items to be edited**</span></span>  
     <span data-ttu-id="57b72-187">指定已簽入的項目可以在記憶體中編輯。</span><span class="sxs-lookup"><span data-stu-id="57b72-187">Specifies that items that are checked in can be edited in memory.</span></span> <span data-ttu-id="57b72-188">如果您選取此核取方塊，當您嘗試編輯簽入的專案時，[**編輯**] 按鈕會出現在 [**簽出**] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="57b72-188">If you select this check box, an **Edit** button appears in the **Check Out** dialog box when you attempt to edit a checked-in item.</span></span> <span data-ttu-id="57b72-189">按一下此按鈕之後，即可編輯項目。</span><span class="sxs-lookup"><span data-stu-id="57b72-189">After clicking this button, you can edit the item.</span></span> <span data-ttu-id="57b72-190">如果您嘗試儲存項目，就必須將項目簽出或儲存到其他位置。</span><span class="sxs-lookup"><span data-stu-id="57b72-190">If you attempt to save the item, you must check it out or save it to a different location.</span></span>  
  
     <span data-ttu-id="57b72-191">**重設**</span><span class="sxs-lookup"><span data-stu-id="57b72-191">**Reset**</span></span>  
     <span data-ttu-id="57b72-192">將原始檔控制確認對話方塊重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="57b72-192">Resets source control confirmation dialog boxes to their default settings.</span></span> <span data-ttu-id="57b72-193">例如，如果您已選取 [原始檔控制] 對話方塊中的 [**不要再顯示此對話方塊]** 核取方塊，選取 [**重設**] 選項會反轉該動作。</span><span class="sxs-lookup"><span data-stu-id="57b72-193">For example, if you have selected the **Don't show this dialog again** check box in a source control dialog box, selecting the **Reset** option reverses that action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b72-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b72-194">See Also</span></span>  
 <span data-ttu-id="57b72-195">[原始檔控制基本概念](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="57b72-195">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="57b72-196">[變更原始檔控制連接](../../2014/database-engine/change-source-control-connections.md) </span><span class="sxs-lookup"><span data-stu-id="57b72-196">[Change Source Control Connections](../../2014/database-engine/change-source-control-connections.md) </span></span>  
 [<span data-ttu-id="57b72-197">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="57b72-197">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
