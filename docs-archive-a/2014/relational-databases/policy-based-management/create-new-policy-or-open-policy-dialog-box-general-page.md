---
title: 建立新原則或開啟原則對話方塊，一般頁面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.newgroup.f1
- sql12.swb.dmf.policy.f1
- sql12.swb.dmf.policy.filter.f1
ms.assetid: c00bebd0-d04b-4c64-840e-8b7a2c603436
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4b67cb8faf18001b841824b806e7befc0683d457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594020"
---
# <a name="create-new-policy-or-open-policy-dialog-box-general-page"></a><span data-ttu-id="cc0ba-102">建立新原則或開啟原則對話方塊，一般頁面</span><span class="sxs-lookup"><span data-stu-id="cc0ba-102">Create New Policy or Open Policy Dialog Box, General Page</span></span>
  <span data-ttu-id="cc0ba-103">使用此對話方塊可建立新的以原則為基礎的管理原則，或是修改現有的原則。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-103">Use this dialog box to create a new Policy-Based Management policy or modify an existing policy.</span></span> <span data-ttu-id="cc0ba-104">使用 **[針對目標]** 和 **[伺服器限制]** 區域當做篩選，將原則限制為所有可能目標的子集。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-104">Use the **Against targets** and **Server restriction** areas as a filter to limit policies to a subset of all possible targets.</span></span> <span data-ttu-id="cc0ba-105">如果是要當做目標篩選使用的條件，必須在實體 Facet 上定義這些條件，而且這些條件不能包含函數和 LIKE 運算子。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-105">For conditions to be used as target filters, they must be defined on a physical facet, must not contain functions, and must not contain the LIKE operator.</span></span> <span data-ttu-id="cc0ba-106">當系統計算原則的物件集時，根據預設會排除系統物件。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-106">When the system computes the object set for a policy, by default the system objects are excluded.</span></span>  <span data-ttu-id="cc0ba-107">例如，如果原則的物件集是指所有資料表，則原則不會套用至系統資料表。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-107">For example, if the object set of the policy refers to all tables, the policy will not apply to system tables.</span></span> <span data-ttu-id="cc0ba-108">如果使用者想要對系統物件評估原則，可以明確地將系統物件加入至物件集。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-108">If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set.</span></span> <span data-ttu-id="cc0ba-109">不過，雖然 **check on schedule** 評估模式支援所有原則，但基於效能的考量， **check on change** 評估模式並未支援所有原則與任意物件集搭配使用。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-109">However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode.</span></span> <span data-ttu-id="cc0ba-110">如需詳細資訊，請參閱 [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span><span class="sxs-lookup"><span data-stu-id="cc0ba-110">For more information, see [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span></span>  
  
## <a name="options"></a><span data-ttu-id="cc0ba-111">選項。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-111">Options</span></span>  
 <span data-ttu-id="cc0ba-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-112">**Name**</span></span>  
 <span data-ttu-id="cc0ba-113">如果是新的原則，請輸入新原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-113">For a new policy, type the new policy name.</span></span> <span data-ttu-id="cc0ba-114">如果是現有的原則，則會顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-114">For an existing policy, the name is displayed.</span></span>  
  
 <span data-ttu-id="cc0ba-115">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-115">**Enabled**</span></span>  
 <span data-ttu-id="cc0ba-116">選取 [已啟用]  核取方塊可啟用此原則。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-116">Select the **Enabled** check box to enable the policy.</span></span> <span data-ttu-id="cc0ba-117">清除 **[已啟用]** 核取方塊可停用此原則。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-117">Clear the **Enabled** check box to disable the policy.</span></span> <span data-ttu-id="cc0ba-118">**[已啟用]** 方塊適用於原則 Automation，</span><span class="sxs-lookup"><span data-stu-id="cc0ba-118">The **Enabled** box applies to policy automation.</span></span> <span data-ttu-id="cc0ba-119">它會建立或移除原則的 Automation 系統。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-119">It creates or removes the automation system for the policy.</span></span> <span data-ttu-id="cc0ba-120">Automation 使用下列機制：</span><span class="sxs-lookup"><span data-stu-id="cc0ba-120">Automation uses the following mechanisms:</span></span>  
  
 <span data-ttu-id="cc0ba-121">**變更時 - 避免**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-121">**On change: prevent**</span></span>  
 <span data-ttu-id="cc0ba-122">資料庫觸發程序會強制執行相容性。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-122">A database trigger enforces compliance.</span></span>  
  
 <span data-ttu-id="cc0ba-123">**變更時 - 僅限記錄**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-123">**On change: log only**</span></span>  
 <span data-ttu-id="cc0ba-124">通知服務事件會檢查相容性。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-124">A notification services event checks for compliance.</span></span>  
  
 <span data-ttu-id="cc0ba-125">**按排程時間**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-125">**On schedule**</span></span>  
 <span data-ttu-id="cc0ba-126">建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業來按排程時間檢查相容性。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-126">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created to check for compliance on a schedule.</span></span>  
  
 <span data-ttu-id="cc0ba-127">使用 **[視需要]** 評估模式執行的原則不會使用這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-127">Policies that are run using **On demand** evaluation mode do not use this check box.</span></span>  
  
 <span data-ttu-id="cc0ba-128">**檢查條件**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-128">**Check condition**</span></span>  
 <span data-ttu-id="cc0ba-129">選取這個原則使用之以原則為基礎的管理條件。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-129">Select the Policy-Based Management condition that this policy uses.</span></span> <span data-ttu-id="cc0ba-130">伺服器上關聯之以原則為基礎之管理 Facet 的條件都會列出來。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-130">All conditions on the server for the associated Policy-Based Management facet are listed.</span></span> <span data-ttu-id="cc0ba-131">按一下 **[新增條件]** 即可建立新條件。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-131">Click **New condition** to create a new condition.</span></span> <span data-ttu-id="cc0ba-132">按一下省略符號 ( **...** ) 按鈕即可修改條件。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-132">Click the ellipsis (**...**) button to modify the condition.</span></span>  
  
 <span data-ttu-id="cc0ba-133">**[針對目標]**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-133">**Against targets**</span></span>  
 <span data-ttu-id="cc0ba-134">選取可供這個 Facet 使用的目標類型，以完成篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-134">Select the target types that are available for this facet to complete a filter expression.</span></span>  
  
 <span data-ttu-id="cc0ba-135">**評估模式**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-135">**Evaluation Mode**</span></span>  
 <span data-ttu-id="cc0ba-136">選取此原則的評估模式。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-136">Select the evaluation mode for the policy.</span></span> <span data-ttu-id="cc0ba-137">某些原則可加以檢查，但不會強制執行。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-137">Some policies can be checked but not enforced.</span></span> <span data-ttu-id="cc0ba-138">評估模式如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc0ba-138">The evaluation modes are as follows:</span></span>  
  
 <span data-ttu-id="cc0ba-139">**[視需要]**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-139">**On demand**</span></span>  
 <span data-ttu-id="cc0ba-140">只有當您從 [評估]  對話方塊執行原則時，才可以執行。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-140">Policy will only be run when you run it from the **Evaluate** dialog box.</span></span>  
  
 <span data-ttu-id="cc0ba-141">**按排程時間**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-141">**On schedule**</span></span>  
 <span data-ttu-id="cc0ba-142">定期評估原則、針對具有不相容的原則記下記錄項目，並建立報表。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-142">Periodically evaluates the policy, records a log entry for policies that have out-of-compliance, and creates a report.</span></span> <span data-ttu-id="cc0ba-143">啟用 **[排程]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-143">Enables the **Schedule** box.</span></span>  
  
 <span data-ttu-id="cc0ba-144">**變更時 - 僅限記錄**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-144">**On change: log only**</span></span>  
 <span data-ttu-id="cc0ba-145">當嘗試變更時，這個選項不會阻止不相容的變更，但是會記錄原則違規。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-145">When changes are tried, this option does not prevent out-of-compliance changes, but logs policy violations.</span></span>  
  
 <span data-ttu-id="cc0ba-146">**變更時 - 避免**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-146">**On change: prevent**</span></span>  
 <span data-ttu-id="cc0ba-147">當嘗試變更時，這個選項會阻止將違反原則的變更。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-147">When changes are tried, this option prevents changes that would violate the policy.</span></span>  
  
 <span data-ttu-id="cc0ba-148">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-148">**Schedule**</span></span>  
 <span data-ttu-id="cc0ba-149">當選取 [按排程時間]  評估模式時會出現這個選項。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-149">This option appears when **On schedule** evaluation mode is selected.</span></span> <span data-ttu-id="cc0ba-150">輸入排程的名稱、按一下 **[挑選]** 從清單中選取排程，或是按一下 **[新增]** 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-150">Type the name of the schedule, click **Pick** to select a schedule from a list, or click **New** to create a new schedule.</span></span> <span data-ttu-id="cc0ba-151">若要啟用排程區域，必須選取 **[按排程時間]** 。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-151">To enable the schedule area, **On schedule** must be selected.</span></span>  
  
 <span data-ttu-id="cc0ba-152">**[伺服器限制]**</span><span class="sxs-lookup"><span data-stu-id="cc0ba-152">**Server restriction**</span></span>  
 <span data-ttu-id="cc0ba-153">選取適合此原則的伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-153">Select the types of servers that are appropriate for this policy.</span></span> <span data-ttu-id="cc0ba-154">選項為 **[無]** 或是選取用來篩選可能之伺服器的條件。</span><span class="sxs-lookup"><span data-stu-id="cc0ba-154">Options are **None** or select a condition that filters the possible servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0ba-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc0ba-155">See Also</span></span>  
 [<span data-ttu-id="cc0ba-156">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="cc0ba-156">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
