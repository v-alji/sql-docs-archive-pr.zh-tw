---
title: 解除安裝現有的 SQL Server 執行個體 (安裝程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51d426a12a2f7f1b7bedbfb7770c4d9cb369f12b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595441"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a><span data-ttu-id="20d29-102">解除安裝現有的 SQL Server 執行個體 (安裝程式)</span><span class="sxs-lookup"><span data-stu-id="20d29-102">Uninstall an Existing Instance of SQL Server (Setup)</span></span>
  <span data-ttu-id="20d29-103">本文描述如何解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的獨立執行個體。</span><span class="sxs-lookup"><span data-stu-id="20d29-103">This article describes how to uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="20d29-104">遵循本主題的步驟，也可以讓系統做好準備，以便可以重新安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20d29-104">By following the steps in this topic, you also prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20d29-105">若要解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體，您必須是本機管理員，且具有以服務登入的權限。</span><span class="sxs-lookup"><span data-stu-id="20d29-105">To uninstall an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be a local administrator with permission to log on as a service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20d29-106">若要解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式所提供的「移除節點」功能來分別移除每個節點。</span><span class="sxs-lookup"><span data-stu-id="20d29-106">To uninstall a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="20d29-107">如需詳細資訊，請參閱[在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="20d29-107">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="20d29-108">解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前，請先考慮下列重要資訊：</span><span class="sxs-lookup"><span data-stu-id="20d29-108">Consider the following important information before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="20d29-109">從實體記憶體數量為最小需求量的電腦中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件前，必須先確定分頁檔案大小是充足的。</span><span class="sxs-lookup"><span data-stu-id="20d29-109">Before you remove [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components from a computer that has the minimum required amount of physical memory, make sure that the page file size is sufficient.</span></span> <span data-ttu-id="20d29-110">分頁檔案大小必須等於實體記憶體數量的兩倍。</span><span class="sxs-lookup"><span data-stu-id="20d29-110">The page file size must be equal to two times the amount of physical memory.</span></span> <span data-ttu-id="20d29-111">虛擬記憶體不足可能會造成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移除不完全。</span><span class="sxs-lookup"><span data-stu-id="20d29-111">Insufficient virtual memory can cause an incomplete removal of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="20d29-112">若有多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 會在解除安裝最後一個 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體時自動解除安裝。</span><span class="sxs-lookup"><span data-stu-id="20d29-112">If you have multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser uninstalls automatically when the last instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is uninstalled.</span></span>  
  
     <span data-ttu-id="20d29-113">如果您想要解除安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的所有元件，您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [控制台] **的** [程式和功能] **中，手動解除安裝**Browser 元件。</span><span class="sxs-lookup"><span data-stu-id="20d29-113">If you want to uninstall all components of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must uninstall the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser component manually from **Programs and Features** in **Control Panel**.</span></span>  
  
### <a name="before-you-uninstall"></a><span data-ttu-id="20d29-114">解除安裝之前</span><span class="sxs-lookup"><span data-stu-id="20d29-114">Before You Uninstall</span></span>  
  
1.  <span data-ttu-id="20d29-115">**備份您的資料。**</span><span class="sxs-lookup"><span data-stu-id="20d29-115">**Back up your data.**</span></span> <span data-ttu-id="20d29-116">雖然這並非必要步驟，不過您可能會擁有要以目前狀態儲存的資料庫，</span><span class="sxs-lookup"><span data-stu-id="20d29-116">Although this is not a required step, you might have databases that you want to save in their present state.</span></span> <span data-ttu-id="20d29-117">也可能想要儲存先前對系統資料庫所做的變更。</span><span class="sxs-lookup"><span data-stu-id="20d29-117">You might also want to save changes that were made to the system databases.</span></span> <span data-ttu-id="20d29-118">若符合其中任一情況，請務必在解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前先行備份資料。</span><span class="sxs-lookup"><span data-stu-id="20d29-118">If either situation is true, make sure that back up the data before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="20d29-119">或者，您也可以將所有資料和記錄檔的複本儲存在 MSSQL 資料夾以外的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="20d29-119">Alternatively, save a copy of all the data and log files in a folder other than the MSSQL folder.</span></span> <span data-ttu-id="20d29-120">解除安裝期間將會刪除 MSSQL 資料夾。</span><span class="sxs-lookup"><span data-stu-id="20d29-120">The MSSQL folder is deleted during uninstallation.</span></span>  
  
     <span data-ttu-id="20d29-121">您必須儲存的檔案包括下列資料庫檔案：</span><span class="sxs-lookup"><span data-stu-id="20d29-121">The files that you must save include the following database files:</span></span>  
  
    -   <span data-ttu-id="20d29-122">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="20d29-122">Master.mdf</span></span>  
  
    -   <span data-ttu-id="20d29-123">Mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="20d29-123">Mastlog.ldf</span></span>  
  
    -   <span data-ttu-id="20d29-124">Model.mdf</span><span class="sxs-lookup"><span data-stu-id="20d29-124">Model.mdf</span></span>  
  
    -   <span data-ttu-id="20d29-125">Modellog.ldf</span><span class="sxs-lookup"><span data-stu-id="20d29-125">Modellog.ldf</span></span>  
  
    -   <span data-ttu-id="20d29-126">Msdbdata.mdf</span><span class="sxs-lookup"><span data-stu-id="20d29-126">Msdbdata.mdf</span></span>  
  
    -   <span data-ttu-id="20d29-127">Msdblog.ldf</span><span class="sxs-lookup"><span data-stu-id="20d29-127">Msdblog.ldf</span></span>  
  
    -   <span data-ttu-id="20d29-128">Mssqlsystemresource.mdf</span><span class="sxs-lookup"><span data-stu-id="20d29-128">Mssqlsystemresource.mdf</span></span>  
  
    -   <span data-ttu-id="20d29-129">Mssqlsustemresource.ldf</span><span class="sxs-lookup"><span data-stu-id="20d29-129">Mssqlsustemresource.ldf</span></span>  
  
    -   <span data-ttu-id="20d29-130">Tempdb.mdf</span><span class="sxs-lookup"><span data-stu-id="20d29-130">Tempdb.mdf</span></span>  
  
    -   <span data-ttu-id="20d29-131">Templog.ldf</span><span class="sxs-lookup"><span data-stu-id="20d29-131">Templog.ldf</span></span>  
  
    -   <span data-ttu-id="20d29-132">`ReportServer[$InstanceName]` (Thisis [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 預設資料庫。 ) </span><span class="sxs-lookup"><span data-stu-id="20d29-132">`ReportServer[$InstanceName]` (Thisis the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default database.)</span></span>  
  
    -   <span data-ttu-id="20d29-133">ReportServer[$InstanceName]TempDB (這是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 預設暫存資料庫)。</span><span class="sxs-lookup"><span data-stu-id="20d29-133">ReportServer[$InstanceName]TempDB (This is the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default temporary database.)</span></span>  
  
2.  <span data-ttu-id="20d29-134">**刪除本機安全性群組。**</span><span class="sxs-lookup"><span data-stu-id="20d29-134">**Delete the local security groups.**</span></span> <span data-ttu-id="20d29-135">在解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前，請先刪除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="20d29-135">Before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], delete the local security groups for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
3.  <span data-ttu-id="20d29-136">**停止所有**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **服務。**</span><span class="sxs-lookup"><span data-stu-id="20d29-136">**Stop all**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services.**</span></span> <span data-ttu-id="20d29-137">：建議您在解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件之前，先停止所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="20d29-137">We recommend that you stop all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="20d29-138">使用中的連接可能會導致解除安裝無法順利完成。</span><span class="sxs-lookup"><span data-stu-id="20d29-138">Active connections can prevent successful uninstallation.</span></span>  
  
4.  <span data-ttu-id="20d29-139">**使用具有適當權限的帳戶。**</span><span class="sxs-lookup"><span data-stu-id="20d29-139">**Use an account that has the appropriate permissions.**</span></span> <span data-ttu-id="20d29-140">請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶或具有同等權限的帳戶登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="20d29-140">Log on to the server by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account or by using an account that has equivalent permissions.</span></span> <span data-ttu-id="20d29-141">例如，您可以使用本機管理員群組成員的帳戶登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="20d29-141">For example, you can log on to the server by using an account that is a member of the local Administrators group.</span></span>  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a><span data-ttu-id="20d29-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d29-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="20d29-143">若要開始解除安裝程序，請移至 **[控制台]** ，然後移至 **[程式和功能]**。</span><span class="sxs-lookup"><span data-stu-id="20d29-143">To begin the uninstall process, go to **Control Panel** and then **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="20d29-144">按一下滑鼠右鍵 **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** ，然後選取 [**卸載**]。</span><span class="sxs-lookup"><span data-stu-id="20d29-144">Right click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** and select **Uninstall**.</span></span> <span data-ttu-id="20d29-145">然後按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="20d29-145">Then click **Remove**.</span></span> <span data-ttu-id="20d29-146">這樣就會啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="20d29-146">This starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
     <span data-ttu-id="20d29-147">安裝程式支援規則將會執行，以便驗證您的電腦組態。</span><span class="sxs-lookup"><span data-stu-id="20d29-147">Setup Support Rules runs to verify your computer configuration.</span></span> <span data-ttu-id="20d29-148">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="20d29-148">To continue, click **Next**.</span></span>  
  
3.  <span data-ttu-id="20d29-149">在 [選取執行個體] 頁面上，使用下拉式方塊來指定要移除的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，或指定僅移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共用功能和管理工具的選項。</span><span class="sxs-lookup"><span data-stu-id="20d29-149">On the Select Instance page, use the drop-down box to specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to remove, or specify the option to remove only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared features and management tools.</span></span> <span data-ttu-id="20d29-150">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="20d29-150">To continue, click **Next**.</span></span>  
  
4.  <span data-ttu-id="20d29-151">在 [選取功能] 頁面上，指定要從指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="20d29-151">On the Select Features page, specify the features to remove from the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="20d29-152">移除規則將會執行，以便確認作業可以順利完成。</span><span class="sxs-lookup"><span data-stu-id="20d29-152">Removal rules runs to verify that the operation can complete successfully.</span></span>  
  
5.  <span data-ttu-id="20d29-153">在 **[準備移除]** 頁面上，檢閱即將解除安裝之元件和功能的清單。</span><span class="sxs-lookup"><span data-stu-id="20d29-153">On the **Ready to Remove** page, review the list of components and features that will be uninstalled.</span></span> <span data-ttu-id="20d29-154">按一下 **[移除]** 開始解除安裝</span><span class="sxs-lookup"><span data-stu-id="20d29-154">Click **Remove** to begin uninstalling</span></span>  
  
6.  <span data-ttu-id="20d29-155">解除安裝最後一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [程式和功能] **的程式清單中仍會顯示與**相關聯的其他程式。</span><span class="sxs-lookup"><span data-stu-id="20d29-155">Immediately after you uninstall the last [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, the other programs associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will still be visible in the list of programs in **Programs and Features**.</span></span> <span data-ttu-id="20d29-156">不過，如果您關閉 **[程式和功能]**，下次再開啟 **[程式和功能]** 時，就會重新整理程式清單，只顯示實際上仍安裝的程式。</span><span class="sxs-lookup"><span data-stu-id="20d29-156">However, if you close **Programs and Features**, the next time you open **Programs and Features**, it will refresh the list of programs, to show only the ones that are actually still installed.</span></span>  
  
### <a name="if-the-uninstallation-fails"></a><span data-ttu-id="20d29-157">如果解除安裝失敗</span><span class="sxs-lookup"><span data-stu-id="20d29-157">If the Uninstallation Fails</span></span>  
  
1.  <span data-ttu-id="20d29-158">如果解除安裝程序未順利完成，請嘗試解決導致解除安裝失敗的問題。</span><span class="sxs-lookup"><span data-stu-id="20d29-158">If the uninstallation process does not complete successfully, attempt to fix the problem that caused the uninstallation to fail.</span></span> <span data-ttu-id="20d29-159">下列文章可以幫助您了解解除安裝失敗的原因：</span><span class="sxs-lookup"><span data-stu-id="20d29-159">The following articles can help you understand the cause of the failed uninstallation:</span></span>  
  
    -   [<span data-ttu-id="20d29-160">如何在安裝記錄檔中識別 SQL Server 2008 的安裝問題</span><span class="sxs-lookup"><span data-stu-id="20d29-160">How to identify SQL Server 2008 setup issues in the setup log files</span></span>](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [<span data-ttu-id="20d29-161">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="20d29-161">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  <span data-ttu-id="20d29-162">如果無法修正解除安裝失敗的原因，您可以連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 支援部門。</span><span class="sxs-lookup"><span data-stu-id="20d29-162">If you are unable to fix the cause of the uninstallation failure, you can contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support.</span></span> <span data-ttu-id="20d29-163">在某些情況下，例如不小心刪除重要的檔案，可能需要先重新安裝作業系統，才能在電腦上重新安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="20d29-163">In some cases, such as unintentional deletion of important files, reinstalling the operating system may be required before reinstalling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d29-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d29-164">See Also</span></span>  
 [<span data-ttu-id="20d29-165">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="20d29-165">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
