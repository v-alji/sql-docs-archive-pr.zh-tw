---
title: 將 PowerPivot 遷移至 SharePoint 2013 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e59c6d6553cc9c43155b059fedf4eb6e124ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688321"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a><span data-ttu-id="1071c-102">將 PowerPivot 移轉至 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1071c-102">Migrate PowerPivot to SharePoint 2013</span></span>


 <span data-ttu-id="1071c-103">SharePoint 2013 不支援就地升級。</span><span class="sxs-lookup"><span data-stu-id="1071c-103">SharePoint 2013 does not support in-place upgrade.</span></span> <span data-ttu-id="1071c-104">不過，**支援資料庫附加升級的程式**。</span><span class="sxs-lookup"><span data-stu-id="1071c-104">However the procedure of **database-attach upgrade is supported**.</span></span> <span data-ttu-id="1071c-105">此行為與升級至 SharePoint 2010 不同，後者的客戶可以在兩種基本升級方法中選擇：就地升級與資料庫附加升級。</span><span class="sxs-lookup"><span data-stu-id="1071c-105">The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in-place upgrade and database-attach upgrade.</span></span>

 <span data-ttu-id="1071c-106">如果您擁有與 SharePoint 2010 整合的 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 安裝，就無法就地升級 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1071c-106">If you have a [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation integrated with SharePoint 2010, you cannot upgrade in-place the SharePoint server.</span></span> <span data-ttu-id="1071c-107">不過，您可以將內容資料庫和伺服器應用程式資料庫從 SharePoint 2010 伺服器陣列移轉至 SharePoint 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="1071c-107">However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.</span></span> <span data-ttu-id="1071c-108">本主題是完成資料庫附加升級以及完成 PowerPivot 相關移轉所需步驟的概觀：</span><span class="sxs-lookup"><span data-stu-id="1071c-108">This topic is an overview of the steps required to complete a database-attach upgrade and complete a migration related to PowerPivot:</span></span>

 <span data-ttu-id="1071c-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1071c-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013</span></span>

### <a name="migration-overview"></a><span data-ttu-id="1071c-110">移轉概觀</span><span class="sxs-lookup"><span data-stu-id="1071c-110">Migration Overview</span></span>

|<span data-ttu-id="1071c-111">1</span><span class="sxs-lookup"><span data-stu-id="1071c-111">1</span></span>|<span data-ttu-id="1071c-112">2</span><span class="sxs-lookup"><span data-stu-id="1071c-112">2</span></span>|<span data-ttu-id="1071c-113">3</span><span class="sxs-lookup"><span data-stu-id="1071c-113">3</span></span>|<span data-ttu-id="1071c-114">4</span><span class="sxs-lookup"><span data-stu-id="1071c-114">4</span></span>|
|-------|-------|-------|-------|
|<span data-ttu-id="1071c-115">準備 SharePoint 2013 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="1071c-115">Prepare the SharePoint 2013 farm</span></span>|<span data-ttu-id="1071c-116">備份、複製和還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-116">Backup, copy, restore databases.</span></span>|<span data-ttu-id="1071c-117">掛接內容資料庫</span><span class="sxs-lookup"><span data-stu-id="1071c-117">Mount content databases</span></span>|<span data-ttu-id="1071c-118">移轉 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 排程</span><span class="sxs-lookup"><span data-stu-id="1071c-118">Migrate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Schedules</span></span>|
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="1071c-119">SharePoint 管理中心</span><span class="sxs-lookup"><span data-stu-id="1071c-119">SharePoint Central Administration</span></span><br /><br /> <span data-ttu-id="1071c-120">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1071c-120">Windows PowerShell</span></span>|<span data-ttu-id="1071c-121">SharePoint 應用程式頁面</span><span class="sxs-lookup"><span data-stu-id="1071c-121">SharePoint application Pages</span></span><br /><br /> <span data-ttu-id="1071c-122">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1071c-122">Windows PowerShell</span></span>|

 <span data-ttu-id="1071c-123">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="1071c-123">**In this topic:**</span></span>

-   [<span data-ttu-id="1071c-124">1) 準備 SharePoint 2013 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="1071c-124">1) Prepare the SharePoint 2013 Farm</span></span>](#bkmk_prepare_sharepoint2013)

-   [<span data-ttu-id="1071c-125">2) 備份、複製和還原資料庫</span><span class="sxs-lookup"><span data-stu-id="1071c-125">2) Backup, Copy, Restore the Databases</span></span>](#bkmk_backup_restore)

-   [<span data-ttu-id="1071c-126">3) 準備 Web 應用程式和掛接內容資料庫</span><span class="sxs-lookup"><span data-stu-id="1071c-126">3) Prepare Web Applications and Mount Content Databases</span></span>](#bkmk_prepare_mount_databases)

-   [<span data-ttu-id="1071c-127">4) 升級 PowerPivot 排程</span><span class="sxs-lookup"><span data-stu-id="1071c-127">4) Upgrade PowerPivot Schedules</span></span>](#bkmk_upgrade_powerpivot_schedules)

-   [<span data-ttu-id="1071c-128">其他資源</span><span class="sxs-lookup"><span data-stu-id="1071c-128">Additional Resources</span></span>](#bkmk_additional_resources)

##  <a name="1-prepare-the-sharepoint-2013-farm"></a><a name="bkmk_prepare_sharepoint2013"></a><span data-ttu-id="1071c-129">1) 準備 SharePoint 2013 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="1071c-129">1) Prepare the SharePoint 2013 Farm</span></span>

1.  > [!TIP]
    >  <span data-ttu-id="1071c-130">請檢閱您現有 Web 應用程式所設定的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="1071c-130">Review the authentication method your existing web applications are configured for.</span></span> <span data-ttu-id="1071c-131">SharePoint 2013 Web 應用程式預設為宣告式驗證。</span><span class="sxs-lookup"><span data-stu-id="1071c-131">SharePoint 2013 web applications default to claims-based authentication.</span></span> <span data-ttu-id="1071c-132">設定為傳統模式驗證的 SharePoint 2010 Web 應用程式需要進行其他步驟，才能將資料庫從 SharePoint 2010 移轉至 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="1071c-132">SharePoint 2010 web applications configured for classic-mode authentication require additional steps to migrate databases from SharePoint 2010 to SharePoint 2013.</span></span> <span data-ttu-id="1071c-133">如果您的 Web 應用程式設定為傳統模式驗證，請檢閱 SharePoint 2013 文件集。</span><span class="sxs-lookup"><span data-stu-id="1071c-133">If your web applications are configured for classic-mode authentication, review the SharePoint 2013 documentation.</span></span>

2.  <span data-ttu-id="1071c-134">安裝新的 SharePoint Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="1071c-134">Install a new SharePoint Server 2013 farm.</span></span>

3.  <span data-ttu-id="1071c-135">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 以 SharePoint 模式安裝伺服器的實例。</span><span class="sxs-lookup"><span data-stu-id="1071c-135">Install an instance of a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="1071c-136">如需詳細資訊，請參閱＜ [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)＞。</span><span class="sxs-lookup"><span data-stu-id="1071c-136">For more information, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

4.  <span data-ttu-id="1071c-137">在 SharePoint 伺服器陣列中的每部伺服器上執行 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 安裝套件 **spPowerPivot.msi** 。</span><span class="sxs-lookup"><span data-stu-id="1071c-137">Run the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 installation package **spPowerPivot.msi** on each server in the SharePoint farm.</span></span> <span data-ttu-id="1071c-138">如需詳細資訊，請參閱[安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="1071c-138">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>

5.  <span data-ttu-id="1071c-139">在 SharePoint 2013 管理中心內，將 Excel Services 服務應用程式設定為使用在先前步驟中建立的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 模式伺服器。</span><span class="sxs-lookup"><span data-stu-id="1071c-139">In SharePoint 2013 Central Administration, configure the Excel Services service application to use the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server created in the previous step.</span></span> <span data-ttu-id="1071c-140">如需詳細資訊，請參閱[PowerPivot for SharePoint 2013 安裝](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)的「設定基本 Analysis Services SharePoint 整合」一節。</span><span class="sxs-lookup"><span data-stu-id="1071c-140">For more information, see the "Configure Basic Analysis Services SharePoint Integration" section of [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

##  <a name="2-backup-copy-restore-the-databases"></a><a name="bkmk_backup_restore"></a><span data-ttu-id="1071c-141">2) 備份、複製、還原資料庫</span><span class="sxs-lookup"><span data-stu-id="1071c-141">2) Backup, Copy, Restore the Databases</span></span>
 <span data-ttu-id="1071c-142">「SharePoint 資料庫附加升級」程式是一系列的步驟，可將 PowerPivot 相關的內容和服務應用程式資料庫備份、複製和還原至 SharePoint 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="1071c-142">The "SharePoint database-attach upgrade" process is a sequence of steps to back up, copy, and restore PowerPivot related content and service application databases to the SharePoint 2013 farm.</span></span>

1.  <span data-ttu-id="1071c-143">**將資料庫設定唯讀：** 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下資料庫名稱，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1071c-143">**Set Database to read-only:** In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name and click **Properties**.</span></span> <span data-ttu-id="1071c-144">在 [選項]\*\*\*\* 頁面上，將 [資料庫唯讀]\*\*\*\* 屬性設定為 [True]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1071c-144">On the **Options** page, set the **Database read-Only** property to **True**.</span></span>

2.  <span data-ttu-id="1071c-145">**備份** ：備份您想要移轉至 SharePoint 2013 伺服器陣列的每個內容資料庫及服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-145">**Back up:** Back up each content database and service application database that you want to migrate to the SharePoint 2013 farm.</span></span> <span data-ttu-id="1071c-146">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下資料庫名稱，按一下 [工作]\*\*\*\*，然後按一下 [備份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1071c-146">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name, click **Tasks**, and click **Back up**.</span></span>

3.  <span data-ttu-id="1071c-147">將資料庫備份檔案 (.bak) 複製到所需的目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="1071c-147">File copy the database backup files (.bak) to the desired destination server.</span></span>

4.  <span data-ttu-id="1071c-148">**還原** ：將資料庫還原至目的地 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1071c-148">**Restore:** Restore the databases to the destination [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="1071c-149">您可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]來完成這個步驟。</span><span class="sxs-lookup"><span data-stu-id="1071c-149">This step can be completed using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

5.  <span data-ttu-id="1071c-150">**將資料庫設定為讀寫：** 將 [資料庫唯讀]\*\*\*\* 設定為 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1071c-150">**Set Database to read-write:** Set the **Database read-Only** to **False**.</span></span>

##  <a name="3-prepare-web-applications-and-mount-content-databases"></a><a name="bkmk_prepare_mount_databases"></a><span data-ttu-id="1071c-151">3) 準備 Web 應用程式和掛接內容資料庫</span><span class="sxs-lookup"><span data-stu-id="1071c-151">3) Prepare Web Applications and Mount Content Databases</span></span>
 <span data-ttu-id="1071c-152">如需下列程式的詳細說明，請參閱將[資料庫從 sharepoint 2010 升級至 sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690) 。</span><span class="sxs-lookup"><span data-stu-id="1071c-152">For a more detailed explanation of the following procedures, see [Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>

1.  <span data-ttu-id="1071c-153">**讓資料庫離線：**</span><span class="sxs-lookup"><span data-stu-id="1071c-153">**Take Databases Offline:**</span></span>

     <span data-ttu-id="1071c-154">使用 SharePoint 管理中心，讓每個 SharePoint 2013 內容資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="1071c-154">Take each SharePoint 2013 content database offline, using SharePoint Central Administration.</span></span> <span data-ttu-id="1071c-155">您所複製的資料庫會取代這些內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-155">The content databases are replaced by the databases you copied over.</span></span> <span data-ttu-id="1071c-156">請針對您的環境考量最佳順序。</span><span class="sxs-lookup"><span data-stu-id="1071c-156">Consider what is the best sequence for your environment.</span></span> <span data-ttu-id="1071c-157">您可以考慮分別讓每個資料庫離線並且掛接其相關的取代資料庫，然後再讓下一個內容資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="1071c-157">Consider taking each database offline and mount its relevant replacement database before taking the next content database offline.</span></span> <span data-ttu-id="1071c-158">另一個選項是以群組的方式，讓所有內容資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="1071c-158">Another option is to take all the content databases offline as a group.</span></span>

    1.  <span data-ttu-id="1071c-159">在 SharePoint 管理中心內，按一下 **[應用程式管理]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-159">In SharePoint Central Administration, click **Application Management**.</span></span>

    2.  <span data-ttu-id="1071c-160">按一下 **[管理內容資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-160">Click **Manage Content Databases**.</span></span>

    3.  <span data-ttu-id="1071c-161">按一下資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1071c-161">Click the name of the database.</span></span>

    4.  <span data-ttu-id="1071c-162">在 **[管理內容資料庫設定]** 上，將 **[資料庫狀態]** 設定為 **[離線]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-162">On the **Manage Content Database Settings**, set **Database status** to **Offline**.</span></span>

    5.  <span data-ttu-id="1071c-163">選取 **[移除內容資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-163">Select **Remove Content Database**.</span></span> <span data-ttu-id="1071c-164">請注意，此時會顯示一則警告，表示儲存在內容資料庫中的網站將無法再存取。</span><span class="sxs-lookup"><span data-stu-id="1071c-164">Note the warning that sites stored in the content database will no longer be accessible.</span></span>

-   <span data-ttu-id="1071c-165">**掛接內容資料庫：**</span><span class="sxs-lookup"><span data-stu-id="1071c-165">**Mount content databases:**</span></span>

     <span data-ttu-id="1071c-166">使用 SharePoint 2013 管理命令介面中的 PowerShell 指令程式來掛接移轉的內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-166">Use PowerShell cmdlets in the SharePoint 2013 Management shell to mount the migrated content database.</span></span> <span data-ttu-id="1071c-167">服務應用程式資料庫不需要裝載，只有內容資料庫： ![PowerShell 相關內容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="1071c-167">The service application database does not need to be mounted, only the content databases: ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>

    ```powershell
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]
    ```

     <span data-ttu-id="1071c-168">如需詳細資訊，請參閱[將內容資料庫附加或卸離 (SharePoint Server 2010) ](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="1071c-168">For more information, see [Attach or detach content databases (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx).</span></span>

     <span data-ttu-id="1071c-169">**完成此步驟之後的狀態**  ：當掛接作業完成時，使用者可以看見原本位於舊內容資料庫中的檔案。</span><span class="sxs-lookup"><span data-stu-id="1071c-169">**Status when the step is complete:**  When the mount operation is complete, users can see files that were in the old content database.</span></span> <span data-ttu-id="1071c-170">因此，使用者可以查看和開啟文件庫中的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="1071c-170">Therefore users can see and open the workbooks in the document library.</span></span>

    > [!TIP]
    >  <span data-ttu-id="1071c-171">此時，移轉程序可能會針對移轉的活頁簿建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="1071c-171">It is possible at this point in the migration process to create new schedules for the migrated workbooks.</span></span> <span data-ttu-id="1071c-172">不過，這些排程是建立在新的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服務應用程式資料庫中，而非您從舊 SharePoint 伺服器陣列所複製的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-172">However, the schedules are created in the new [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application database, and not the database you copied from the old SharePoint farm.</span></span> <span data-ttu-id="1071c-173">因此，資料庫不會包含任何舊排程。</span><span class="sxs-lookup"><span data-stu-id="1071c-173">Therefore it will not contain any of the old schedules.</span></span> <span data-ttu-id="1071c-174">在您完成下列步驟以使用舊資料庫並移轉舊排程之後，則無法使用新的排程。</span><span class="sxs-lookup"><span data-stu-id="1071c-174">After you complete the following steps to use the old database and migrate the old schedules, the new schedules are not available.</span></span>

### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a><span data-ttu-id="1071c-175">疑難排解嘗試掛接資料庫時所發生的問題</span><span class="sxs-lookup"><span data-stu-id="1071c-175">Troubleshoot issues when you attempt to mount databases</span></span>
 <span data-ttu-id="1071c-176">本節將摘要說明掛接資料庫時可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="1071c-176">This section summarizes possible issues encountered when mounting the database.</span></span>

1.  <span data-ttu-id="1071c-177">**驗證錯誤** ：如果您看見與驗證有關的錯誤，請檢閱來源 Web 應用程式所使用的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="1071c-177">**Authentication errors:** If you see errors related to authentication, review what authentication mode the source web applications are using.</span></span> <span data-ttu-id="1071c-178">此錯誤可能是由於 SharePoint 2013 Web 應用程式與 SharePoint 2010 Web 應用程式之間的驗證不符所造成。</span><span class="sxs-lookup"><span data-stu-id="1071c-178">The error could be caused by a mismatch in authentication between the SharePoint 2013 web application and the SharePoint 2010 web application.</span></span> <span data-ttu-id="1071c-179">如需詳細資訊，請參閱＜ [1) 準備 SharePoint 2013 伺服器陣列](#bkmk_prepare_sharepoint2013) ＞。</span><span class="sxs-lookup"><span data-stu-id="1071c-179">See the [1) Prepare the SharePoint 2013 Farm](#bkmk_prepare_sharepoint2013) for more information.</span></span>

2.  <span data-ttu-id="1071c-180">**遺漏 PowerPivot 檔案：** 如果您看見與遺漏 PowerPivot .dll 有關的錯誤，就表示尚未安裝 **spPowerPivot.msi** ，或者尚未使用 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 組態工具來設定 PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="1071c-180">**Missing PowerPivot.Files:** If you see errors related to missing PowerPivot .dlls, the **spPowerPivot.msi** has not been installed or the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Configuration Tool has not been used to configure PowerPivot.</span></span>

##  <a name="4-upgrade-powerpivot-schedules"></a><a name="bkmk_upgrade_powerpivot_schedules"></a><span data-ttu-id="1071c-181">4) 升級 PowerPivot 排程</span><span class="sxs-lookup"><span data-stu-id="1071c-181">4) Upgrade PowerPivot Schedules</span></span>
 <span data-ttu-id="1071c-182">本節將描述移轉 PowerPivot 排程的詳細資料和選項。</span><span class="sxs-lookup"><span data-stu-id="1071c-182">This section describes the details and options for migrating PowerPivot schedules.</span></span> <span data-ttu-id="1071c-183">排程移轉是兩個步驟的程序。</span><span class="sxs-lookup"><span data-stu-id="1071c-183">Schedule migration is a two-step process.</span></span> <span data-ttu-id="1071c-184">首先，請將 PowerPivot 服務應用程式設定為使用移轉的服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-184">First configure the PowerPivot service application to use the migrated service application database.</span></span> <span data-ttu-id="1071c-185">接著，請選擇兩個排程移轉選項的其中之一。</span><span class="sxs-lookup"><span data-stu-id="1071c-185">Second, choose one of two options for schedule migration.</span></span>

 <span data-ttu-id="1071c-186">**將服務應用程式設定為使用移轉的服務應用程式資料庫。**</span><span class="sxs-lookup"><span data-stu-id="1071c-186">**Configure the service application to use the migrated service application database.**</span></span>

 <span data-ttu-id="1071c-187">在 SharePoint 管理中心內，將 PowerPivot 服務應用程式設定為使用您所複製的舊服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-187">In SharePoint Central Administration to configure the PowerPivot services application to use the old service application database you copied over.</span></span> <span data-ttu-id="1071c-188">PowerPivot 服務會將服務應用程式資料庫升級為新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1071c-188">The PowerPivot Service upgrades the service application database to the new schema.</span></span>

1.  <span data-ttu-id="1071c-189">在 SharePoint 管理中心內，按一下 [管理服務應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1071c-189">In SharePoint Central Administration, click **Manage Service Applications**.</span></span>

2.  <span data-ttu-id="1071c-190">尋找 PowerPivot 服務應用程式（例如「預設的 PowerPivot 服務應用程式」），按一下服務應用程式的名稱，然後按一下 SharePoint 功能區中的 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1071c-190">Find the PowerPivot service application, for example "Default PowerPivot Service Application", click the name of the service application and click **Properties** in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="1071c-191">將資料庫伺服器名稱-執行個體以及資料庫名稱更新為</span><span class="sxs-lookup"><span data-stu-id="1071c-191">Update the database server name-instance and the database name.</span></span> <span data-ttu-id="1071c-192">您所備份、複製和還原的正確資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1071c-192">To the correct names for the database you backed up, copied, and restored.</span></span> <span data-ttu-id="1071c-193">一旦您按一下 **[確定]** 之後，就會升級服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-193">Once you click **Ok**, the service application database is upgraded.</span></span> <span data-ttu-id="1071c-194">錯誤將列在 ULS 記錄中。</span><span class="sxs-lookup"><span data-stu-id="1071c-194">Errors will be in the ULS log.</span></span>

 <span data-ttu-id="1071c-195">**升級 PowerPivot 排程**</span><span class="sxs-lookup"><span data-stu-id="1071c-195">**Upgrade PowerPivot schedules**</span></span>

 <span data-ttu-id="1071c-196">設定 PowerPivot 服務應用程式以移轉重新整理排程。</span><span class="sxs-lookup"><span data-stu-id="1071c-196">Configure the PowerPivot service application to migrate refresh schedules.</span></span>

-   <span data-ttu-id="1071c-197">**移轉排程選項 1：SharePoint 伺服器陣列管理員**</span><span class="sxs-lookup"><span data-stu-id="1071c-197">**Migrate Schedules option1: SharePoint farm administrator**</span></span>

    1.  <span data-ttu-id="1071c-198">在 SharePoint 2013 管理中，執行 `Set-PowerPivotServiceApplication` 具有參數的 Cmdlet `-StartMigratingRefreshSchedules` ，以啟用自動隨選排程遷移![PowerShell 相關內容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")。</span><span class="sxs-lookup"><span data-stu-id="1071c-198">In the SharePoint 2013 Management Run the `Set-PowerPivotServiceApplication` cmdlet with the `-StartMigratingRefreshSchedules` switch to enable automatic on demand schedule migration ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content").</span></span> <span data-ttu-id="1071c-199">下列 Windows PowerShell 指令碼會假設只有一個 PowerPivot 服務應用程式存在。</span><span class="sxs-lookup"><span data-stu-id="1071c-199">The following Windows PowerShell script assumes that there is only one PowerPivot service application.</span></span>

        ```powershell
        $app = Get-PowerPivotServiceApplication
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules
        ```

         <span data-ttu-id="1071c-200">執行 Windows PowerShell 指令碼之後，排程就會處於使用中狀態，而且排程會在下一個適當的時間執行。</span><span class="sxs-lookup"><span data-stu-id="1071c-200">After the Windows PowerShell script is run, the schedules are active and the schedules will run at the next appropriate time.</span></span> <span data-ttu-id="1071c-201">不過，排程重新整理頁面上的狀態並非 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="1071c-201">However, the status one the schedule refresh page is not enabled.</span></span> <span data-ttu-id="1071c-202">當排程第一次執行時，它將進行移轉，而且在排程重新整理頁面上，[ **已啟用**  ] 將會成立。</span><span class="sxs-lookup"><span data-stu-id="1071c-202">When the schedule runs the first time it will be migrated and on the schedule refresh page, **Enabled**  will be true.</span></span>

    2.  <span data-ttu-id="1071c-203">如果您想要檢查 StartMigratingRefreshSchedules 屬性的目前值，請執行下列 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1071c-203">If you want to check the current value of the StartMigratingRefreshSchedules property, run the following PowerShell script.</span></span> <span data-ttu-id="1071c-204">這個指令碼會在所有 PowerPivot 服務應用程式物件中執行迴圈，並且顯示名稱和屬性值：</span><span class="sxs-lookup"><span data-stu-id="1071c-204">The Script loops through all PowerPivot service application objects and display the name and property values:</span></span>

        ```powershell
        $apps = Get-PowerPivotServiceApplication
        foreach ($app in $apps){ Get-PowerPivotServiceApplication $app | Format-Table -Property displayname, id, StartMigratingRefreshSchedules }
        ```

     <span data-ttu-id="1071c-205">**移轉排程選項 2：使用者更新每個活頁簿**</span><span class="sxs-lookup"><span data-stu-id="1071c-205">**Migrate Schedules option2: User updates each workbook**</span></span>

    1.  <span data-ttu-id="1071c-206">另一個移轉排程的選項是針對每個活頁簿啟用排程重新整理。</span><span class="sxs-lookup"><span data-stu-id="1071c-206">Another option to migrate schedules is to enable the schedule refresh for each workbook.</span></span> <span data-ttu-id="1071c-207">導覽到包含活頁簿的文件庫。</span><span class="sxs-lookup"><span data-stu-id="1071c-207">Navigate to the document library that contains the workbooks.</span></span>

    2.  <span data-ttu-id="1071c-208">開啟操作功能表，然後按一下 **[管理 PowerPivot 資料重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-208">Open the context menu and click **Manage PowerPivot Data Refresh**.</span></span>

    3.  <span data-ttu-id="1071c-209">在 **[排程重新整理]** 區段中，按一下 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-209">In the **schedule refresh** section, click **Enable**.</span></span>

    4.  <span data-ttu-id="1071c-210">您可以選取 **[並且盡快重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="1071c-210">You can select **Also refresh as soon as possible**.</span></span> <span data-ttu-id="1071c-211">一旦您按一下 [確定] 之後，這個選項就會將一個重新整理執行個體加入至佇列。</span><span class="sxs-lookup"><span data-stu-id="1071c-211">This option adds one instance of the refresh to the queue as soon as you click ok.</span></span> <span data-ttu-id="1071c-212">定期重新整理排程仍然會在適當的時間觸發。</span><span class="sxs-lookup"><span data-stu-id="1071c-212">The regular refresh schedule still triggers at the appropriate time.</span></span>

    5.  <span data-ttu-id="1071c-213">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1071c-213">Click **Ok**.</span></span> <span data-ttu-id="1071c-214">重新整理記錄現在會顯示在重新整理頁面中，而且排程會在一般時間引發。</span><span class="sxs-lookup"><span data-stu-id="1071c-214">The refresh history is now visible in the refresh page, the schedule will fire at the normal time.</span></span>

 <span data-ttu-id="1071c-215">**SQL Server 2008 R2 PowerPivot 活頁簿**</span><span class="sxs-lookup"><span data-stu-id="1071c-215">**SQL Server 2008 R2 PowerPivot workbooks**</span></span>

-   <span data-ttu-id="1071c-216">在 SQL Server 2012 SP1 PowerPivot for SharePoint 2013 中使用 SQL Server 2008 R2 PowerPivot 活頁簿時，這些活頁簿不會自動升級。</span><span class="sxs-lookup"><span data-stu-id="1071c-216">SQL Server 2008 R2 PowerPivot workbooks do not automatically upgrade when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="1071c-217">當您移轉包含 2008 R2 活頁簿的內容資料庫之後，就可以使用這些活頁簿，但是排程不會升級。</span><span class="sxs-lookup"><span data-stu-id="1071c-217">After you migrate a content database containing the 2008 R2 workbooks, you can use the workbooks but the schedules do not upgrade.</span></span>

-   <span data-ttu-id="1071c-218">如需詳細資訊，請參閱 [升級活頁簿和排程的資料重新整理 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="1071c-218">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> <span data-ttu-id="1071c-219">其他資源</span><span class="sxs-lookup"><span data-stu-id="1071c-219">Additional Resources</span></span>

> [!NOTE]
>  <span data-ttu-id="1071c-220">如需有關 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 和 SharePoint 資料庫附加升級的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1071c-220">For more information on [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] and SharePoint database-attach upgrade, see the following:</span></span>

-   <span data-ttu-id="1071c-221">[升級活頁簿和排程的資料重新整理 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)</span><span class="sxs-lookup"><span data-stu-id="1071c-221">[Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

-   <span data-ttu-id="1071c-222">[SharePoint 2013 (的升級程式總覽](https://go.microsoft.com/fwlink/p/?LinkId=256688) https://go.microsoft.com/fwlink/p/?LinkId=256688) 。</span><span class="sxs-lookup"><span data-stu-id="1071c-222">[Overview of the upgrade process to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).</span></span>

-   <span data-ttu-id="1071c-223">[升級至 SharePoint 2013 (之前，請先清除準備](https://go.microsoft.com/fwlink/p/?LinkId=256689)工作 https://go.microsoft.com/fwlink/p/?LinkId=256689) 。</span><span class="sxs-lookup"><span data-stu-id="1071c-223">[Clean up preparations before an upgrade to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).</span></span>

-   <span data-ttu-id="1071c-224">[將資料庫從 sharepoint 2010 升級至 sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690) 。</span><span class="sxs-lookup"><span data-stu-id="1071c-224">[Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>
