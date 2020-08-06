---
title: 刪除資料層應用程式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 602256c287a8c7bcf9d3fa5597b2fec2085c626c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705169"
---
# <a name="delete-a-data-tier-application"></a><span data-ttu-id="35a7d-102">刪除資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="35a7d-102">Delete a Data-tier Application</span></span>
  <span data-ttu-id="35a7d-103">您可以使用 [刪除資料層應用程式精靈] 或 Windows PowerShell 指令碼來刪除資料層應用程式。</span><span class="sxs-lookup"><span data-stu-id="35a7d-103">You can delete a data-tier application by using either the Delete Data-tier Application wizard or a Windows PowerShell script.</span></span> <span data-ttu-id="35a7d-104">您可以指定是否要保留、卸離或卸除相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="35a7d-104">You can specify whether the associated database is retained, detached, or dropped.</span></span>  
  
-   <span data-ttu-id="35a7d-105">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="35a7d-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="35a7d-106">**若要升級 DAC，請使用下列方式：** [註冊資料層應用程式精靈](#UsingDeleteDACWizard)、[PowerShell](#DeleteDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="35a7d-106">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="35a7d-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="35a7d-107">Before You Begin</span></span>  
 <span data-ttu-id="35a7d-108">當您刪除資料層應用程式 (DAC) 執行個體時，可以選擇三個選項中的一個，指定要使用與資料層應用程式相關聯之資料庫執行的動作。</span><span class="sxs-lookup"><span data-stu-id="35a7d-108">When you delete a data-tier application (DAC) instance, you choose one of three options specifying what is to be done with the database associated with the data-tier application.</span></span> <span data-ttu-id="35a7d-109">所有的三個選項都會刪除 DAC 定義中繼資料。</span><span class="sxs-lookup"><span data-stu-id="35a7d-109">All three options delete the DAC definition metadata.</span></span> <span data-ttu-id="35a7d-110">這些選項的差異在於它們使用與資料層應用程式相關聯之資料庫執行的動作。</span><span class="sxs-lookup"><span data-stu-id="35a7d-110">The options differ in what they do with the database associated with the data-tier application.</span></span> <span data-ttu-id="35a7d-111">精靈不會刪除與 DAC 或資料庫相關聯的任何執行個體層級物件，例如登入。</span><span class="sxs-lookup"><span data-stu-id="35a7d-111">The wizard does not delete any of the instance-level objects associated with the DAC or database, such as logins.</span></span>  
  
|<span data-ttu-id="35a7d-112">選項</span><span class="sxs-lookup"><span data-stu-id="35a7d-112">Option</span></span>|<span data-ttu-id="35a7d-113">資料庫動作</span><span class="sxs-lookup"><span data-stu-id="35a7d-113">Database actions</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="35a7d-114">刪除註冊</span><span class="sxs-lookup"><span data-stu-id="35a7d-114">Delete registration</span></span>|<span data-ttu-id="35a7d-115">相關聯的資料庫會保持不變。</span><span class="sxs-lookup"><span data-stu-id="35a7d-115">The associated database remains intact.</span></span>|  
|<span data-ttu-id="35a7d-116">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="35a7d-116">Detach database</span></span>|<span data-ttu-id="35a7d-117">相關聯的資料庫會遭到卸離。</span><span class="sxs-lookup"><span data-stu-id="35a7d-117">The associated database is detached.</span></span> <span data-ttu-id="35a7d-118">Database Engine 執行個體無法參考資料庫，但是資料和記錄檔保持不變。</span><span class="sxs-lookup"><span data-stu-id="35a7d-118">The instance of the Database Engine cannot reference the database, but the data and log files are intact.</span></span>|  
|<span data-ttu-id="35a7d-119">刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="35a7d-119">Delete database</span></span>|<span data-ttu-id="35a7d-120">相關聯的資料庫會遭到卸除。</span><span class="sxs-lookup"><span data-stu-id="35a7d-120">The associated database is dropped.</span></span> <span data-ttu-id="35a7d-121">資料和記錄檔會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="35a7d-121">The data and log files are deleted.</span></span>|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="35a7d-122">限制事項</span><span class="sxs-lookup"><span data-stu-id="35a7d-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="35a7d-123">在刪除 DAC 之後還原 DAC 定義中繼資料或資料庫沒有任何自動化的機制。</span><span class="sxs-lookup"><span data-stu-id="35a7d-123">There is no automatic mechanism to restore the DAC definition metadata or the database after you delete a DAC.</span></span> <span data-ttu-id="35a7d-124">您手動重建 DAC 執行個體的方式取決於刪除選項。</span><span class="sxs-lookup"><span data-stu-id="35a7d-124">How you can manually rebuild the DAC instance depends on the delete option.</span></span>  
  
|<span data-ttu-id="35a7d-125">選項</span><span class="sxs-lookup"><span data-stu-id="35a7d-125">Option</span></span>|<span data-ttu-id="35a7d-126">如何重建 DAC 執行個體</span><span class="sxs-lookup"><span data-stu-id="35a7d-126">How to Rebuild the DAC Instance</span></span>|  
|------------|-------------------------------------|  
|<span data-ttu-id="35a7d-127">刪除註冊</span><span class="sxs-lookup"><span data-stu-id="35a7d-127">Delete registration</span></span>|<span data-ttu-id="35a7d-128">從原狀的資料庫註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-128">Register a DAC from the database left in place.</span></span>|  
|<span data-ttu-id="35a7d-129">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="35a7d-129">Detach database</span></span>|<span data-ttu-id="35a7d-130">使用 **sp_attachdb** 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]重新附加資料庫，然後從資料庫註冊新的 DAC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a7d-130">Re-attach the database by using **sp_attachdb** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then register a new DAC instance from the database.</span></span>|  
|<span data-ttu-id="35a7d-131">刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="35a7d-131">Delete database</span></span>|<span data-ttu-id="35a7d-132">從刪除 DAC 之前所做的完整備份還原資料庫，然後從資料庫註冊新的 DAC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a7d-132">Restore the database from a full backup made before the DAC was deleted, and then register a new DAC instance from the database.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="35a7d-133">從已還原或重新附加的資料庫註冊 DAC 來重建 DAC 執行個體時，將無法重新建立原始 DAC 的某些部分，例如伺服器選取原則。</span><span class="sxs-lookup"><span data-stu-id="35a7d-133">Rebuilding a DAC instance by registering a DAC from a restored or re-attached database will not recreate some parts of the original DAC, such as the server selection policy.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="35a7d-134">權限</span><span class="sxs-lookup"><span data-stu-id="35a7d-134">Permissions</span></span>  
 <span data-ttu-id="35a7d-135">DAC 只能由系統管理員 ( **sysadmin** ) 或伺服器管理員 ( **serveradmin** ) 固定伺服器角色的成員或資料庫擁有者刪除。</span><span class="sxs-lookup"><span data-stu-id="35a7d-135">A DAC can only be deleted by members of the **sysadmin** or **serveradmin** fixed server roles, or by the database owner.</span></span> <span data-ttu-id="35a7d-136">名為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的內建** 系統管理員帳戶也可以啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="35a7d-136">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also launch the wizard.</span></span>  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> <span data-ttu-id="35a7d-137">使用刪除資料層應用程式精靈</span><span class="sxs-lookup"><span data-stu-id="35a7d-137">Using the Delete Data-tier Application Wizard</span></span>  
 <span data-ttu-id="35a7d-138">**使用精靈刪除 DAC**</span><span class="sxs-lookup"><span data-stu-id="35a7d-138">**To Delete a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="35a7d-139">在 **[物件總管]** 中，展開含有要刪除的 DAC 之執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="35a7d-139">In **Object Explorer**, expand the node for the instance containing the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="35a7d-140">展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="35a7d-140">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="35a7d-141">展開 **資料層應用程式** 節點。</span><span class="sxs-lookup"><span data-stu-id="35a7d-141">Expand the **Data-tier Applications** node.</span></span>  
  
4.  <span data-ttu-id="35a7d-142">以滑鼠右鍵按一下要刪除的 DAC，然後選取 [刪除資料層應用程式…] </span><span class="sxs-lookup"><span data-stu-id="35a7d-142">Right-click the DAC to be deleted, and then select **Delete Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="35a7d-143">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="35a7d-143">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="35a7d-144">簡介</span><span class="sxs-lookup"><span data-stu-id="35a7d-144">Introduction</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="35a7d-145">選擇方法</span><span class="sxs-lookup"><span data-stu-id="35a7d-145">Choose Method</span></span>](#Choose_method)  
  
    3.  [<span data-ttu-id="35a7d-146">總結</span><span class="sxs-lookup"><span data-stu-id="35a7d-146">Summary</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="35a7d-147">刪除資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="35a7d-147">Delete Data-tier Application</span></span>](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="35a7d-148">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="35a7d-148">Introduction Page</span></span>  
 <span data-ttu-id="35a7d-149">此頁面描述刪除資料層應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="35a7d-149">This page describes the steps for deleting a data-tier application.</span></span>  
  
 <span data-ttu-id="35a7d-150">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="35a7d-150">**Do not show this page again.**</span></span> <span data-ttu-id="35a7d-151">- 按一下此核取方塊，之後就不會再顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="35a7d-151">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="35a7d-152">**下一步 >** - 繼續進行至 [選擇方法]  頁面。</span><span class="sxs-lookup"><span data-stu-id="35a7d-152">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="35a7d-153">**取消** - 結束精靈，不刪除資料層應用程式或資料庫。</span><span class="sxs-lookup"><span data-stu-id="35a7d-153">**Cancel** - Ends the wizard without deleting a data-tier application or database.</span></span>  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a> <span data-ttu-id="35a7d-154">選擇方法頁面</span><span class="sxs-lookup"><span data-stu-id="35a7d-154">Choose Method Page</span></span>  
 <span data-ttu-id="35a7d-155">使用此頁面來指定用於處理與要刪除的 DAC 相關聯之資料庫的選項。</span><span class="sxs-lookup"><span data-stu-id="35a7d-155">Use this page to specify the option for handling the database associated with the DAC to be deleted.</span></span>  
  
 <span data-ttu-id="35a7d-156">**刪除註冊** - 移除定義資料層應用程式的中繼資料，但讓相關聯的資料庫保持不變。</span><span class="sxs-lookup"><span data-stu-id="35a7d-156">**Delete registration** - Removes the metadata defining the data-tier application, but leaves the associated database intact.</span></span>  
  
 <span data-ttu-id="35a7d-157">**卸離資料庫** - 移除定義資料層應用程式的中繼資料，並卸離相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="35a7d-157">**Detach database** - Removes the metadata defining the data-tier application and detaches the associated database.</span></span>  
  
 <span data-ttu-id="35a7d-158">該 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體無法再參考資料庫，但資料和記錄檔保持不變。</span><span class="sxs-lookup"><span data-stu-id="35a7d-158">The database can no longer be referenced by that instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but the data and log files remain intact.</span></span>  
  
 <span data-ttu-id="35a7d-159">**刪除資料庫** - 移除定義 DAC 的中繼資料，並卸除相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="35a7d-159">**Delete database** - Removes the metadata defining the DAC and drops the associated database.</span></span>  
  
 <span data-ttu-id="35a7d-160">資料庫的資料和記錄檔會遭到永久刪除。</span><span class="sxs-lookup"><span data-stu-id="35a7d-160">The data and log files for the database are permanently deleted.</span></span>  
  
 <span data-ttu-id="35a7d-161">\*\* \< 上一步**-返回 [**簡介\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="35a7d-161">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="35a7d-162">**下一步 >** - 繼續進行 [摘要]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="35a7d-162">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="35a7d-163">**取消** - 結束精靈，不刪除 DAC 或資料庫。</span><span class="sxs-lookup"><span data-stu-id="35a7d-163">**Cancel** - Ends the wizard without deleting the DAC or database.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="35a7d-164">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="35a7d-164">Summary Page</span></span>  
 <span data-ttu-id="35a7d-165">使用此頁面來檢閱刪除 DAC 執行個體時，精靈將會採取的動作。</span><span class="sxs-lookup"><span data-stu-id="35a7d-165">Use this page to review the actions the wizard will take when deleting the DAC instance.</span></span>  
  
 <span data-ttu-id="35a7d-166">**檢閱選項摘要** - 檢閱顯示在方塊中的 DAC、資料庫與刪除方法。</span><span class="sxs-lookup"><span data-stu-id="35a7d-166">**Review your selection summary** - Review the DAC, database, and deletion method displayed in the box.</span></span> <span data-ttu-id="35a7d-167">如果資訊正確，選取 **[下一步]** 或 **[完成]** 來刪除 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-167">If the information is correct, select either **Next** or **Finish** to delete the DAC.</span></span> <span data-ttu-id="35a7d-168">如果 DAC 和資料庫資訊不正確，選取 **[取消]** ，然後選取正確的 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-168">If the DAC and database information is not correct, select **Cancel** and select the correct DAC.</span></span> <span data-ttu-id="35a7d-169">如果刪除方法不正確，選取 **[上一步]** ，返回 **[選擇方法]** 頁面，然後選取其他方法。</span><span class="sxs-lookup"><span data-stu-id="35a7d-169">If the deletion method is not correct, select **Previous** to return to the **Choose Method** page and select a different method.</span></span>  
  
 <span data-ttu-id="35a7d-170">\*\* \< 上一步**-返回 [**選擇方法\*\*] 頁面，選擇不同的 delete 方法。</span><span class="sxs-lookup"><span data-stu-id="35a7d-170">**\< Previous** - Returns to the **Choose Method** page to choose a different delete method.</span></span>  
  
 <span data-ttu-id="35a7d-171">**下一步 >** - 使用您在上一頁選擇的方法刪除 DAC 執行個體，然後繼續進行 [刪除資料層應用程式]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="35a7d-171">**Next >** - Deletes the DAC instance using the method you chose on the previous page, and proceeds to the **Delete Data-tier Application** page.</span></span>  
  
 <span data-ttu-id="35a7d-172">**取消** - 結束精靈，不刪除 DAC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a7d-172">**Cancel** - Ends the wizard without deleting the DAC instance.</span></span>  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a><span data-ttu-id="35a7d-173">刪除資料層應用程式頁面</span><span class="sxs-lookup"><span data-stu-id="35a7d-173">Delete Data-tier Application Page</span></span>  
 <span data-ttu-id="35a7d-174">此頁面會報告刪除作業成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="35a7d-174">This page reports the success or failure of the delete operation.</span></span>  
  
 <span data-ttu-id="35a7d-175">**刪除 DAC** - 報告為刪除 DAC 執行個體所採取的每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="35a7d-175">**Deleting the DAC** - Reports the success or failure of each action taken to delete the DAC instance.</span></span> <span data-ttu-id="35a7d-176">檢閱資訊以判斷每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="35a7d-176">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="35a7d-177">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="35a7d-177">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="35a7d-178">選取連結來檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="35a7d-178">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="35a7d-179">**儲存報表** - 選取此按鈕可以將刪除報告儲存到 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="35a7d-179">**Save Report** - Select this button to save the deletion report to an HTML file.</span></span> <span data-ttu-id="35a7d-180">此檔案會報告每個動作的狀態，包括所有動作所產生的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a7d-180">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="35a7d-181">預設資料夾為 Windows 帳戶之文件資料夾中的 SQL Server Management Studio\DAC Packages 資料夾。</span><span class="sxs-lookup"><span data-stu-id="35a7d-181">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account..</span></span>  
  
 <span data-ttu-id="35a7d-182">**完成** - 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="35a7d-182">**Finish** - Ends the wizard.</span></span>  
  
##  <a name="delete-a-dac-using-powershell"></a><a name="DeleteDACPowerShell"></a><span data-ttu-id="35a7d-183">使用 PowerShell 刪除 DAC</span><span class="sxs-lookup"><span data-stu-id="35a7d-183">Delete a DAC Using PowerShell</span></span>  
 <span data-ttu-id="35a7d-184">**使用 PowerShell 指令碼刪除 DAC**</span><span class="sxs-lookup"><span data-stu-id="35a7d-184">**To delete a DAC using a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="35a7d-185">建立 SMO Server 物件，並將它設定為包含要刪除之 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a7d-185">Create a SMO Server object and set it to the instance that contains the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="35a7d-186">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a7d-186">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="35a7d-187">使用 `add_DacActionStarted` 和 `add_DacActionFinished` 訂閱 DAC 升級事件。</span><span class="sxs-lookup"><span data-stu-id="35a7d-187">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
4.  <span data-ttu-id="35a7d-188">指定要刪除的 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-188">Specify the DAC to delete.</span></span>  
  
5.  <span data-ttu-id="35a7d-189">請根據適用的刪除選項，使用下列其中一組程式碼：</span><span class="sxs-lookup"><span data-stu-id="35a7d-189">Use one of these three sets of code, depending on which delete option is appropriate:</span></span>  
  
    -   <span data-ttu-id="35a7d-190">若要刪除 DAC 註冊但讓資料庫保持不變，請使用 `Unmanage()` 方法。</span><span class="sxs-lookup"><span data-stu-id="35a7d-190">To delete the DAC registration but leave the database intact, use the `Unmanage()` method.</span></span>  
  
    -   <span data-ttu-id="35a7d-191">若要刪除 DAC 註冊並卸離資料庫，請使用 `Uninstall()` 方法並指定 `DetachDatabase`。</span><span class="sxs-lookup"><span data-stu-id="35a7d-191">To delete the DAC registration and detach the database, use the `Uninstall()` method and specify `DetachDatabase`.</span></span>  
  
    -   <span data-ttu-id="35a7d-192">若要刪除 DAC 註冊並卸除資料庫，請使用 `Uninstall()` 方法並指定 `DropDatabase`。</span><span class="sxs-lookup"><span data-stu-id="35a7d-192">To delete the DAC registration and drop the database, use the `Uninstall()` method and specify `DropDatabase`.</span></span>  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a><span data-ttu-id="35a7d-193">刪除 DAC 但保留資料庫的範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="35a7d-193">Example Deleting the DAC but Leaving the Database (PowerShell)</span></span>  
 <span data-ttu-id="35a7d-194">下列範例使用 `Unmanage()` 方法刪除 DAC 但讓資料庫保持不變，以刪除名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-194">The following example deletes a DAC named MyApplication using the `Unmanage()` method to delete the DAC but leave the database intact.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a><span data-ttu-id="35a7d-195">刪除 DAC 並卸離資料庫的範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="35a7d-195">Example Deleting the DAC and Detaching the Database (PowerShell)</span></span>  
 <span data-ttu-id="35a7d-196">下列範例使用 `Uninstall()` 方法刪除 DAC 並卸離資料庫，以刪除名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-196">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and detach the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a><span data-ttu-id="35a7d-197">刪除 DAC 並卸除資料庫的範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="35a7d-197">Example Deleting the DAC and Dropping the Database (PowerShell)</span></span>  
 <span data-ttu-id="35a7d-198">下列範例使用 `Uninstall()` 方法刪除 DAC 並卸除資料庫，以刪除名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="35a7d-198">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and drop the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a><span data-ttu-id="35a7d-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a7d-199">See Also</span></span>  
 <span data-ttu-id="35a7d-200">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="35a7d-200">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="35a7d-201">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="35a7d-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="35a7d-202">[部署資料層應用程式](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="35a7d-202">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="35a7d-203">[將資料庫註冊為 DAC](register-a-database-as-a-dac.md) </span><span class="sxs-lookup"><span data-stu-id="35a7d-203">[Register a Database As a DAC](register-a-database-as-a-dac.md) </span></span>  
 <span data-ttu-id="35a7d-204">[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="35a7d-204">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="35a7d-205">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="35a7d-205">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
