---
title: 卸載 PowerPivot for SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3941a2f0-0d0c-4d1a-8618-7a6a7751beac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ca65a04578cbce2ed7eb2831068260d9f0e445a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595437"
---
# <a name="uninstall-powerpivot-for-sharepoint"></a><span data-ttu-id="04f7f-102">解除安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="04f7f-102">Uninstall PowerPivot for SharePoint</span></span>
  <span data-ttu-id="04f7f-103">解除安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 安裝是一個多步驟的作業，其中包括準備解除安裝、從伺服器陣列移除功能和方案，以及移除程式檔案與登錄設定。</span><span class="sxs-lookup"><span data-stu-id="04f7f-103">Uninstalling a [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installation is a multi-step operation that includes preparing for uninstall, removing features and solutions from the farm, and removing program files and registry settings.</span></span>  
  
 <span data-ttu-id="04f7f-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="04f7f-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="04f7f-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="04f7f-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="04f7f-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="04f7f-106">Prerequisites</span></span>](#prereq)  
  
-   [<span data-ttu-id="04f7f-107">步驟 1：解除安裝前的檢查清單</span><span class="sxs-lookup"><span data-stu-id="04f7f-107">Step 1: Pre-Uninstall Checklist</span></span>](#bkmk_before)  
  
-   [<span data-ttu-id="04f7f-108">步驟 2：從 SharePoint 移除功能和方案</span><span class="sxs-lookup"><span data-stu-id="04f7f-108">Step 2: Remove Features and Solutions from SharePoint</span></span>](#bkmk_remove)  
  
-   [<span data-ttu-id="04f7f-109">步驟 3：執行 SQL Server 安裝程式以便從本機電腦移除程式</span><span class="sxs-lookup"><span data-stu-id="04f7f-109">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>](#bkmk_uninstall)  
  
-   [<span data-ttu-id="04f7f-110">步驟 4：解除安裝 PowerPivot for SharePoint 增益集</span><span class="sxs-lookup"><span data-stu-id="04f7f-110">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>](#bkmk_addin)  
  
-   [<span data-ttu-id="04f7f-111">步驟 5：確認解除安裝</span><span class="sxs-lookup"><span data-stu-id="04f7f-111">Step 5: Verify Uninstall</span></span>](#verify)  
  
-   [<span data-ttu-id="04f7f-112">步驟 6：解除安裝後的檢查清單</span><span class="sxs-lookup"><span data-stu-id="04f7f-112">Step 6: Post-Uninstall Checklist</span></span>](#bkmk_post)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="04f7f-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="04f7f-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="04f7f-114">您必須是 SharePoint 伺服器陣列管理員或服務應用程式管理員，才能解除安裝伺服器陣列中的功能和方案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-114">You must be a SharePoint farm administrator or service application administrator to uninstall features and solutions in the farm.</span></span>  
  
-   <span data-ttu-id="04f7f-115">如果您要一併解除安裝 Database Engine，則必須是 SQL Server 系統管理員和本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="04f7f-115">You must be a SQL Server System Administrator and a member of the local Administrators group if you are also uninstalling the Database Engine.</span></span>  
  
-   <span data-ttu-id="04f7f-116">您必須是 Analysis Services 系統管理員和本機 Administrators 群組的成員，才能解除安裝 Analysis Services 和 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="04f7f-116">You must be an Analysis Services System Administrator and a member of the local Administrators group to uninstall Analysis Services and [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span>  
  
##  <a name="step-1-pre-uninstall-checklist"></a><a name="bkmk_before"></a> <span data-ttu-id="04f7f-117">步驟 1：解除安裝前的檢查清單</span><span class="sxs-lookup"><span data-stu-id="04f7f-117">Step 1: Pre-Uninstall Checklist</span></span>  
 <span data-ttu-id="04f7f-118">一旦支援查詢及資料處理的軟體從伺服器陣列中移除之後，就會停用 PowerPivot 資料存取。</span><span class="sxs-lookup"><span data-stu-id="04f7f-118">PowerPivot data access will be disabled once the software that supports query and data processing is removed from the farm.</span></span> <span data-ttu-id="04f7f-119">因此第一步，您必須先刪除不再運作的檔案及文件庫。</span><span class="sxs-lookup"><span data-stu-id="04f7f-119">As a first step, you should preemptively delete files and libraries that will no longer be operational.</span></span> <span data-ttu-id="04f7f-120">此動作有助於解決解除安裝此軟體之前所發生任何有關「資料遺失」的問題。</span><span class="sxs-lookup"><span data-stu-id="04f7f-120">This lets you address any questions or concerns about 'missing data' before you uninstall the software.</span></span>  
  
1.  <span data-ttu-id="04f7f-121">刪除所有與 PowerPivot for SharePoint 安裝有關的 PowerPivot 活頁簿、文件及文件庫。</span><span class="sxs-lookup"><span data-stu-id="04f7f-121">Delete all PowerPivot workbooks, documents, and libraries that are associated with a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="04f7f-122">此軟體一經解除安裝，所有文件庫及文件皆無法再行運作。</span><span class="sxs-lookup"><span data-stu-id="04f7f-122">Neither the libraries nor the documents will function once the software is uninstalled.</span></span>  
  
    -   [<span data-ttu-id="04f7f-123">刪除 PowerPivot 圖庫</span><span class="sxs-lookup"><span data-stu-id="04f7f-123">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="04f7f-124">刪除 PowerPivot 資料摘要庫</span><span class="sxs-lookup"><span data-stu-id="04f7f-124">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
2.  <span data-ttu-id="04f7f-125">刪除其他包含或參照 PowerPivot 資料之文件庫內的 Excel 活頁簿或 Reporting Services 報告。</span><span class="sxs-lookup"><span data-stu-id="04f7f-125">Delete Excel workbooks or Reporting Services reports in other libraries that contain or reference PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="04f7f-126">移除 PerformancePoint 儀表板中任何參照 PowerPivot 資料的網頁組件。</span><span class="sxs-lookup"><span data-stu-id="04f7f-126">Remove any web part in a PerformancePoint dashboard that references PowerPivot data.</span></span>  
  
4.  <span data-ttu-id="04f7f-127">檢視現有網站及文件庫的 SharePoint 權限，確認有無需要變更。</span><span class="sxs-lookup"><span data-stu-id="04f7f-127">Review SharePoint permissions on existing sites and libraries to determine whether you need to change them.</span></span> <span data-ttu-id="04f7f-128">某些 PowerPivot 資料存取狀況 (特別是透過 URL 連接字串對其他活頁簿中之 PowerPivot 資料所進行的次要資料存取) 會需要高於「檢視」權限 (此權限通常會指派給只造訪網站的使用者) 的「讀取」權限。</span><span class="sxs-lookup"><span data-stu-id="04f7f-128">Some PowerPivot data access scenarios, particularly secondary data access via a URL connection string to PowerPivot data in another workbook, require Read permissions, which is higher than the View permissions that are typically assigned to SharePoint users who only visit a site.</span></span> <span data-ttu-id="04f7f-129">您若是不再需要「讀取」權限，可以視情況降低權限。</span><span class="sxs-lookup"><span data-stu-id="04f7f-129">If you no longer require Read permissions, you can reduce permissions accordingly.</span></span>  
  
5.  <span data-ttu-id="04f7f-130">您也可選擇停止服務，然後等候數日之後再解除安裝此軟體。</span><span class="sxs-lookup"><span data-stu-id="04f7f-130">Optionally, stop the services and wait several days before uninstalling the software.</span></span> <span data-ttu-id="04f7f-131">這不是解除安裝的必要步驟，但可以讓您在解決先前未完全解決的資料移轉或技術代換問題時，暫時恢復服務。</span><span class="sxs-lookup"><span data-stu-id="04f7f-131">This step is not necessary for uninstall, but it gives you the option of temporarily resuming the service while you work out any data migration or technology substitution issues that you might have missed.</span></span>  
  
##  <a name="step-2-remove-features-and-solutions-from-sharepoint"></a><a name="bkmk_remove"></a> <span data-ttu-id="04f7f-132">步驟 2：從 SharePoint 移除功能和方案</span><span class="sxs-lookup"><span data-stu-id="04f7f-132">Step 2: Remove Features and Solutions from SharePoint</span></span>  
 <span data-ttu-id="04f7f-133">使用 PowerPivot 組態工具，從 SharePoint 中移除 PowerPivot 服務和應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f7f-133">Use the PowerPivot Configuration Tool to remove PowerPivot services and applications from SharePoint.</span></span>  
  
-   <span data-ttu-id="04f7f-134">您必須是伺服器陣列管理員、Analysis Services 執行個體的伺服器管理員，以及伺服器陣列組態資料庫的 **db_owner**。</span><span class="sxs-lookup"><span data-stu-id="04f7f-134">You must be a farm administrator, a server administrator on the Analysis Services instance, and **db_owner** on the farm's configuration database.</span></span>  
  
-   <span data-ttu-id="04f7f-135">請針對 SharePoint 版本使用適當版本的組態工具。</span><span class="sxs-lookup"><span data-stu-id="04f7f-135">Use the appropriate version of the configuration tool for the version of SharePoint.</span></span> <span data-ttu-id="04f7f-136">請勿將其中任何一個工具用於 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="04f7f-136">Do not use either tool with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] installations.</span></span>  
  
-   <span data-ttu-id="04f7f-137">確認 SharePoint Administration Service 正在執行中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-137">Verify that the SharePoint Administration service is running.</span></span>  
  
1.  <span data-ttu-id="04f7f-138">**執行組態工具：** 請注意，只有當 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 安裝在本機伺服器上時，才會列出組態工具。請在 **[開始]** 功能表上，指向 **[所有程式]** ，依序按一下 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[組態工具]** ，然後按一下下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="04f7f-138">**Run the Configuration tool:** Note the configuration tools are only listed only when [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is installed on the local server.On the **Start** menu, point to **All Programs**, click [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click one of the following:</span></span>  
  
    -   <span data-ttu-id="04f7f-139">**PowerPivot for SharePoint 2013 設定**</span><span class="sxs-lookup"><span data-stu-id="04f7f-139">**PowerPivot for SharePoint 2013 Configuration**</span></span>  
  
    -   <span data-ttu-id="04f7f-140">**PowerPivot 組態工具**</span><span class="sxs-lookup"><span data-stu-id="04f7f-140">**PowerPivot Configuration Tool**</span></span>  
  
2.  <span data-ttu-id="04f7f-141">選取 **[移除功能、服務、應用程式和方案]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="04f7f-141">Select **Remove Features, Services, Applications, and Solutions** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="04f7f-142">或者，將視窗展開為全螢幕。</span><span class="sxs-lookup"><span data-stu-id="04f7f-142">Optionally, expand the window to full size.</span></span> <span data-ttu-id="04f7f-143">您應該會在視窗底部看到一個按鈕列，其中包含 **[驗證]** 、 **[執行]** 和 **[結束]** 命令。</span><span class="sxs-lookup"><span data-stu-id="04f7f-143">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="04f7f-144">檢閱工作清單中的每個動作以了解每個動作的用途。</span><span class="sxs-lookup"><span data-stu-id="04f7f-144">Review each action in the task list to understand what each one does.</span></span>  
  
     <span data-ttu-id="04f7f-145">在 **[移除 PowerPivot 服務應用程式]** 中，您可以選擇刪除與服務應用程式相關聯的應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="04f7f-145">In **Remove PowerPivot Service Applications**, you are given the option of deleting application data associated with the service application.</span></span> <span data-ttu-id="04f7f-146">應用程式資料是使用服務應用程式建立的 SQL Server 資料庫，用於儲存資料重新整理排程、資料庫執行個體資訊、使用量資料，以及 PowerPivot for SharePoint 所使用的其他資料。</span><span class="sxs-lookup"><span data-stu-id="04f7f-146">The application data is a SQL Server database that was created with the service application for the purpose of storing data refresh schedules, database instance information, usage data, and other data used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="04f7f-147">它不會儲存使用者檔案，例如 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="04f7f-147">It does not store user files, such as PowerPivot workbooks.</span></span> <span data-ttu-id="04f7f-148">除非您有保留應用程式資料的特定原因 (例如，如果您有與資料重新整理或資料存取相關的資料保留原則)，您才可以在不移除 SharePoint 使用者所建立或儲存之任何檔案的情況下刪除應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="04f7f-148">Unless you have a specific reason to keep the application data (for example, if you have data retention policies related to data refresh or data access) you can delete the application database without removing any files that were created or saved by SharePoint users.</span></span>  
  
     <span data-ttu-id="04f7f-149">若要刪除資料庫，選取 **[移除 PowerPivot 服務應用程式]** ，然後選取 **[刪除與這個服務應用程式關聯的應用程式資料]**。</span><span class="sxs-lookup"><span data-stu-id="04f7f-149">To delete the database, select **Remove PowerPivot Service Applications** and then select the **Delete application data associated with this service application**.</span></span>  
  
5.  <span data-ttu-id="04f7f-150">或者，在 **[輸出]** 索引標籤或 **[指令碼]** 索引標籤中檢閱詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="04f7f-150">Optionally, review detailed information in the **Output** tab or **Script** tab.</span></span>  
  
     <span data-ttu-id="04f7f-151">[輸出] 索引標籤是此工具即將執行之動作的摘要。</span><span class="sxs-lookup"><span data-stu-id="04f7f-151">The Output tab is a summary of the actions that will be performed by the tool.</span></span> <span data-ttu-id="04f7f-152">此資訊會儲存在記錄檔中：</span><span class="sxs-lookup"><span data-stu-id="04f7f-152">This information is saved in log files at:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Log`  
  
     <span data-ttu-id="04f7f-153">[指令碼] 索引標籤會顯示 PowerShell 指令程式，或參考此工具將執行的 PowerShell 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-153">The Script tab shows the PowerShell cmdlets or references the PowerShell script files that the tool will run.</span></span>  
  
6.  <span data-ttu-id="04f7f-154">按一下 **[驗證]** 來檢查每個動作是否有效。</span><span class="sxs-lookup"><span data-stu-id="04f7f-154">Click **Validate** to check whether each action is valid.</span></span> <span data-ttu-id="04f7f-155">如果無法使用 **[驗證]** ，表示所有動作都適用於您的系統。</span><span class="sxs-lookup"><span data-stu-id="04f7f-155">If **Validate** is not available, it means that all of the actions are valid for your system.</span></span>  
  
7.  <span data-ttu-id="04f7f-156">按一下 **[執行]** ，執行適用於此工作的所有動作。</span><span class="sxs-lookup"><span data-stu-id="04f7f-156">Click **Run** to perform all of the actions that are valid for this task.</span></span> <span data-ttu-id="04f7f-157">只有在通過驗證檢查的情況下，才可以使用 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="04f7f-157">**Run** is available only after the validation check is passed.</span></span> <span data-ttu-id="04f7f-158">當您按一下 [執行]  時，會出現下列警告，提醒您動作是在批次模式下處理：「工具中標示為有效的所有組態設定都會套用到 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="04f7f-158">When you click **Run**, the following warning appears, reminding you that actions are processed in batch mode: "All of the configuration settings that are flagged as valid in the tool will be applied to the SharePoint farm.</span></span> <span data-ttu-id="04f7f-159">您要繼續嗎？」</span><span class="sxs-lookup"><span data-stu-id="04f7f-159">Do you want to continue?"</span></span>  
  
8.  <span data-ttu-id="04f7f-160">按一下 **[是]** 繼續。</span><span class="sxs-lookup"><span data-stu-id="04f7f-160">Click **Yes** to continue.</span></span>  
  
 <span data-ttu-id="04f7f-161">**疑難排解錯誤：**</span><span class="sxs-lookup"><span data-stu-id="04f7f-161">**Troubleshooting errors:**</span></span>  
  
 <span data-ttu-id="04f7f-162">您可以在組態工具的 [參數] 窗格中檢視每個動作的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="04f7f-162">In the Configuration Tool, you can view error information in the Parameters pane for each action.</span></span> <span data-ttu-id="04f7f-163">針對與方案部署或撤銷相關的問題，請確認已啟動 SharePoint Administration 服務。</span><span class="sxs-lookup"><span data-stu-id="04f7f-163">For problems related to solution deployment or retraction, verify the SharePoint Administration service is started.</span></span> <span data-ttu-id="04f7f-164">此服務會執行觸發伺服器陣列中組態變更的計時器作業。</span><span class="sxs-lookup"><span data-stu-id="04f7f-164">This service runs the timer jobs that trigger configuration changes in a farm.</span></span> <span data-ttu-id="04f7f-165">如果該服務未執行，方案部署或撤銷將會失敗。</span><span class="sxs-lookup"><span data-stu-id="04f7f-165">If the service is not running, solution deployment or retraction will fail.</span></span> <span data-ttu-id="04f7f-166">持續性錯誤指的是現有的部署或撤銷作業已經在佇列中，因此會攔截組態工具的其他動作。</span><span class="sxs-lookup"><span data-stu-id="04f7f-166">Persistent errors indicate that an existing deployment or retraction job is already in the queue and blocking further action from the configuration tool.</span></span> <span data-ttu-id="04f7f-167">您可以使用下列 PowerShell 命令來確認服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-167">You can use the following PowerShell command to verify the service is running.</span></span>  
  
```powershell
Get-Service | Where {$_.displayname -like "*sharepoint* administration*"}  
```  
  
 <span data-ttu-id="04f7f-168">若要尋找並移除已經在佇列中的部署或撤銷作業，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="04f7f-168">To find and remove a deployment or retraction job that is already in the queue, do the following:</span></span>  
  
1.  <span data-ttu-id="04f7f-169">至於其他所有錯誤，請檢查 ULS 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="04f7f-169">For all other errors, check the ULS logs.</span></span> <span data-ttu-id="04f7f-170">如需詳細資訊，請參閱[設定及查看 SharePoint 記錄檔和診斷記錄 &#40;PowerPivot for SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging)。</span><span class="sxs-lookup"><span data-stu-id="04f7f-170">For more information, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging).</span></span>  
  
2.  <span data-ttu-id="04f7f-171">以管理員身分啟動 SharePoint 管理命令介面，然後執行下列命令來檢視佇列中的作業：</span><span class="sxs-lookup"><span data-stu-id="04f7f-171">Start the SharePoint Management Shell as an administrator and then run the following command to view jobs in the queue:</span></span>  
  
    ```cmd
    stsadm -o enumdeployments  
    ```  
  
3.  <span data-ttu-id="04f7f-172">檢閱現有部署中的下列資訊： **[類型]** 是 [撤銷] 或 [部署]、 **[檔案]** 是 powerpivotwebapp.wsp 或 powerpivotfarm.wsp。</span><span class="sxs-lookup"><span data-stu-id="04f7f-172">Review existing deployments for the following information: **Type** is Retraction or Deployment, **File** is powerpivotwebapp.wsp or powerpivotfarm.wsp.</span></span>  
  
4.  <span data-ttu-id="04f7f-173">針對與 PowerPivot 方案相關的部署或若是方案撤銷，複製**JobId**的 GUID 值，然後將它貼入下列命令 (使用 Shell 的 [編輯] 功能表上的 [標記]、[複製] 和 [貼上] 命令，將 GUID 複製) ：</span><span class="sxs-lookup"><span data-stu-id="04f7f-173">For deployments or retractions related to PowerPivot solutions, copy the GUID value for **JobId** and then paste it into the following command (use the Mark, Copy, and Paste commands on the Shell's Edit menu to copy the GUID):</span></span>  
  
    ```cmd
    stsadm -o canceldeployment -id "<GUID>"  
    ```  
  
5.  <span data-ttu-id="04f7f-174">依序按一下 **[驗證]** 和 **[執行]** ，重試組態工具中的工作。</span><span class="sxs-lookup"><span data-stu-id="04f7f-174">Retry the task in the configuration tool by clicking **Validate** followed by **Run**.</span></span>  
  
 <span data-ttu-id="04f7f-175">或者，您可以使用 PowerShell 從伺服器陣列移除功能和方案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-175">Alternatively, you can use PowerShell to remove features and solutions from the farm.</span></span> <span data-ttu-id="04f7f-176">如需詳細資訊，請參閱[PowerPivot for SharePoint 的 PowerShell 參考](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="04f7f-176">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
##  <a name="step-3-run-sql-server-setup-to-remove-programs-from-the-local-computer"></a><a name="bkmk_uninstall"></a> <span data-ttu-id="04f7f-177">步驟 3：執行 SQL Server 安裝程式以便從本機電腦移除程式</span><span class="sxs-lookup"><span data-stu-id="04f7f-177">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>  
 <span data-ttu-id="04f7f-178">刪除程式檔案需要您執行 SQL Server 安裝程式來解除安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="04f7f-178">Deleting program files requires that you run SQL Server Setup to uninstall the software.</span></span> <span data-ttu-id="04f7f-179">解除安裝會移除安裝程式所建立的檔案和登錄項目。</span><span class="sxs-lookup"><span data-stu-id="04f7f-179">Uninstall removes both files and the registry entries that were created by Setup.</span></span> <span data-ttu-id="04f7f-180">您可以使用 [程式和功能] 頁面解除安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="04f7f-180">You can use the Programs and Features page to uninstall the software.</span></span> <span data-ttu-id="04f7f-181">安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 是安裝 SQL Server 的一部分。</span><span class="sxs-lookup"><span data-stu-id="04f7f-181">An installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is part of a SQL Server installation.</span></span>  
  
 <span data-ttu-id="04f7f-182">您可以解除安裝部分安裝，而不影響已安裝的其他 SQL Server 執行個體 (或同一個執行個體中的功能)。</span><span class="sxs-lookup"><span data-stu-id="04f7f-182">You can uninstall part of an installation without impacting other SQL Server instances (or features in the same instance) that are already installed.</span></span> <span data-ttu-id="04f7f-183">例如，您可以解除安裝 PowerPivot for SharePoint，但保留安裝其他元件，例如 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或 Database Engine。</span><span class="sxs-lookup"><span data-stu-id="04f7f-183">For example, you can uninstall PowerPivot for SharePoint while leaving other components, such as [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or the Database Engine, installed.</span></span>  
  
1.  <span data-ttu-id="04f7f-184">從程式清單中選取 [Microsoft SQL Server 2014 (64 位元)]  。</span><span class="sxs-lookup"><span data-stu-id="04f7f-184">Select **Microsoft SQL Server 2014 (64-bit)** from the program list.</span></span>  
  
2.  <span data-ttu-id="04f7f-185">按一下 [解除安裝/變更]  。</span><span class="sxs-lookup"><span data-stu-id="04f7f-185">Click **Uninstall/Change**.</span></span>  
  
3.  <span data-ttu-id="04f7f-186">按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="04f7f-186">Click **Remove**.</span></span> <span data-ttu-id="04f7f-187">隨即啟動 SQL Server 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="04f7f-187">This starts SQL Server Setup.</span></span>  
  
     <span data-ttu-id="04f7f-188">您可以從安裝程式選取 **[PowerPivot]** 執行個體，然後選取 **[Analysis Services]** 和 **[Analysis Services SharePoint 整合]** 只移除該功能，而保留其他所有功能。</span><span class="sxs-lookup"><span data-stu-id="04f7f-188">From Setup, you can select the **PowerPivot** instance, and then select **Analysis Services** and **Analysis Services SharePoint Integration** to remove just that feature, leaving everything else in place.</span></span>  
  
##  <a name="step-4-uninstall-the-powerpivot-for-sharepoint-add-in"></a><a name="bkmk_addin"></a><span data-ttu-id="04f7f-189">步驟4：卸載 PowerPivot for SharePoint 增益集</span><span class="sxs-lookup"><span data-stu-id="04f7f-189">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>  
 <span data-ttu-id="04f7f-190">如果您的 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 部署包含兩部以上的伺服器，而且已安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 增益集，請從 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 增益集安裝所在的每一部伺服器上解除安裝增益集，以便完整解除安裝所有 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 檔案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-190">If your [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] deployment has two or more servers and you installed the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Add-in, then uninstall the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] add-in from each server where it was installed to completely uninstall all [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] files.</span></span> <span data-ttu-id="04f7f-191">如需詳細資訊，請參閱[安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="04f7f-191">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>  
  
##  <a name="step-5-verify-uninstall"></a><a name="verify"></a> <span data-ttu-id="04f7f-192">步驟 5：確認解除安裝</span><span class="sxs-lookup"><span data-stu-id="04f7f-192">Step 5: Verify Uninstall</span></span>  
  
1.  <span data-ttu-id="04f7f-193">在 [管理中心] 的 **[管理伺服器上的服務]** 中，連接到您要解除安裝 PowerPivot for SharePoint 所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="04f7f-193">In Central Administration, in **Manage services on server**, connect to the server from which you uninstalled PowerPivot for SharePoint.</span></span>  
  
2.  -   <span data-ttu-id="04f7f-194">如果您解除安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013，請確認清單中不再出現 **[SQL Server PowerPivot 系統服務]** 。</span><span class="sxs-lookup"><span data-stu-id="04f7f-194">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013, verify that **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
    -   <span data-ttu-id="04f7f-195">如果您解除安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010，請確認 **[SQL Server Analysis Services]** 和 **[SQL Server PowerPivot 系統服務]** 都不再出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-195">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010, verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
3.  <span data-ttu-id="04f7f-196">在伺服陣列中解除安裝最後一個的 PowerPivot for SharePoint 伺服器之後，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="04f7f-196">After you uninstall the last PowerPivot for SharePoint server in the farm, do the following:</span></span>  
  
    1.  <span data-ttu-id="04f7f-197">在 [應用程式管理] 的 **[管理服務應用程式]** 中，確認 PowerPivot 服務應用程式不再出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-197">In Application Management, in **Manage service applications**, verify that PowerPivot Service Application no longer appears in the list.</span></span>  
  
    2.  <span data-ttu-id="04f7f-198">在 [系統設定] 的 **[管理伺服器陣列功能]** 中，確認 PowerPivot 整合功能不再出現在頁面上。</span><span class="sxs-lookup"><span data-stu-id="04f7f-198">In System Settings, in **Manage farm features**, verify that PowerPivot Integration Feature is no longer on the page.</span></span> <span data-ttu-id="04f7f-199">在 **[管理伺服器陣列方案]** 中，確認 PowerPivot 方案不再出現在頁面中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-199">In **Manage farm solutions**, verify that the PowerPivot solutions no longer appear on the page.</span></span>  
  
    3.  <span data-ttu-id="04f7f-200">在 [監視] 的 **[設定診斷記錄]** 和 **[設定使用量和健全資料收集]** 中，確認 PowerPivot 事件和事件類別目錄不再出現。</span><span class="sxs-lookup"><span data-stu-id="04f7f-200">In Monitoring, in **Configure diagnostic logging** and in **Configure usage and health data collection**, verify that PowerPivot events and event categories no longer appear.</span></span>  
  
    4.  <span data-ttu-id="04f7f-201">在 [一般應用程式設定] 中，確認 **[PowerPivot 管理儀表板]** 不再出現在頁面中。</span><span class="sxs-lookup"><span data-stu-id="04f7f-201">In General Application Settings, verify that **PowerPivot Management Dashboard** is no longer on the page.</span></span>  
  
##  <a name="step-6-post-uninstall-checklist"></a><a name="bkmk_post"></a> <span data-ttu-id="04f7f-202">步驟 6：解除安裝後的檢查清單</span><span class="sxs-lookup"><span data-stu-id="04f7f-202">Step 6: Post-Uninstall Checklist</span></span>  
 <span data-ttu-id="04f7f-203">使用下列清單移除解除安裝期間未刪除的軟體與檔案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-203">Use the following list to remove software and files that were not deleted during uninstall.</span></span>  
  
1.  <span data-ttu-id="04f7f-204">刪除 `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`中的所有資料檔和子資料夾，然後再刪除該資料夾。</span><span class="sxs-lookup"><span data-stu-id="04f7f-204">Delete all data files and subfolders from `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`, and then delete the folder.</span></span> <span data-ttu-id="04f7f-205">此步驟也會刪除先前快取在 DATA 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="04f7f-205">This step also deletes previously cached files in the DATA directory.</span></span>  
  
2.  <span data-ttu-id="04f7f-206">若還未刪除所有的 PowerPivot 活頁簿、文件及文件庫，請執行此動作。</span><span class="sxs-lookup"><span data-stu-id="04f7f-206">Delete all PowerPivot workbooks, documents, and libraries if you have not already done so.</span></span>  
  
    -   [<span data-ttu-id="04f7f-207">刪除 PowerPivot 圖庫</span><span class="sxs-lookup"><span data-stu-id="04f7f-207">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="04f7f-208">刪除 PowerPivot 資料摘要庫</span><span class="sxs-lookup"><span data-stu-id="04f7f-208">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
3.  <span data-ttu-id="04f7f-209">在 Secure Store Service 中，刪除所有包含 PowerPivot for SharePoint 所使用之預存認證的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f7f-209">In Secure Store Service, delete any target applications that contain stored credentials used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="04f7f-210">當您解除安裝 PowerPivot for SharePoint 時，就會刪除 Secure Store Service 中的某些項目，但不會全部刪除。</span><span class="sxs-lookup"><span data-stu-id="04f7f-210">Some, but not all, entries in Secure Store Service are deleted when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="04f7f-211">專為 PowerPivot 自動重新整理資料帳戶所建立的目標應用程式，以及所有您針對重新整理資料所建立的目標應用程式若仍然存在，應手動予以刪除。</span><span class="sxs-lookup"><span data-stu-id="04f7f-211">Target applications created for the PowerPivot unattended data refresh account plus any target applications you created for data refresh still exist and must be deleted manually.</span></span>  
  
     <span data-ttu-id="04f7f-212">相反地，由 PowerPivot 系統服務自動產生的各種目標應用程式將會在解除安裝 PowerPivot 時自動刪除。</span><span class="sxs-lookup"><span data-stu-id="04f7f-212">In contrast, individual target applications that were auto-generated by the PowerPivot System Service are deleted automatically when PowerPivot is uninstalled.</span></span>  
  
4.  <span data-ttu-id="04f7f-213">在 [控制台] 中，按一下 **[程式]** ，然後按一下 **[解除安裝程式]**</span><span class="sxs-lookup"><span data-stu-id="04f7f-213">In Control Panel, click **Programs**, and then click **Uninstall a program.**</span></span> <span data-ttu-id="04f7f-214">解除安裝所有不再使用的 Analysis Services 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="04f7f-214">Uninstall any Analysis Services client libraries that are no longer used.</span></span> <span data-ttu-id="04f7f-215">當您解除安裝 PowerPivot for SharePoint 時，不會移除 Analysis Services ADOMD.NET 及 Microsoft SQL Server Analysis Management Objects。</span><span class="sxs-lookup"><span data-stu-id="04f7f-215">Analysis Services ADOMD.NET and Microsoft SQL Server Analysis Management Objects are not removed when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="04f7f-216">由於其他使用 Analysis Services 資料的程式庫仍可能需要使用這些程式庫，因此 SQL Server 安裝程式不會自動解除安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="04f7f-216">Because the libraries might be used by other programs that use Analysis Services data, SQL Server Setup does not uninstall them automatically.</span></span> <span data-ttu-id="04f7f-217">如果您不再需要這些用戶端程式庫，必須手動解除安裝它們。</span><span class="sxs-lookup"><span data-stu-id="04f7f-217">You must uninstall these client libraries individually if you no longer need them.</span></span>  
  
     <span data-ttu-id="04f7f-218">除非疑難排解或安裝指示要求您解除安裝 SQL Server Reporting Services SharePoint 2010 增益集，否則請勿任意解除安裝。</span><span class="sxs-lookup"><span data-stu-id="04f7f-218">Do not uninstall the SQL Server Reporting Services SharePoint 2010 Add-in unless you are following troubleshooting or installation instructions that specifically direct you to uninstall it.</span></span> <span data-ttu-id="04f7f-219">Access Services 需要使用 Reporting Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="04f7f-219">The Reporting Services Add-in is used by Access Services.</span></span> <span data-ttu-id="04f7f-220">此增益集由 SharePoint 產品準備工具所安裝，應繼續保留在系統上，以支援 SharePoint 所需要的功能。</span><span class="sxs-lookup"><span data-stu-id="04f7f-220">It is installed by the SharePoint Products Preparation tool and should remain on the system to support functionality required by SharePoint.</span></span>  
  
     <span data-ttu-id="04f7f-221">請勿解除安裝 Analysis Services OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="04f7f-221">Do not uninstall the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="04f7f-222">由 SharePoint 所安裝的 OLE DB 提供者，是連接至 Analysis Services 資料庫之 Excel 活頁簿的必要條件。</span><span class="sxs-lookup"><span data-stu-id="04f7f-222">SharePoint installs the OLE DB provider as a prerequisite for Excel workbooks that connect to Analysis Services databases.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="04f7f-223">所安裝的版本較新，並具備回溯相容性，因此應保留在系統上，以避免日後發生資料連接問題。</span><span class="sxs-lookup"><span data-stu-id="04f7f-223">installs a newer version, but this version is backwards compatible so you should leave it on the system to avoid data connection problems later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f7f-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04f7f-224">See Also</span></span>  
 <span data-ttu-id="04f7f-225">[安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="04f7f-225">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="04f7f-226">PowerPivot 設定工具</span><span class="sxs-lookup"><span data-stu-id="04f7f-226">PowerPivot Configuration Tools</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)  
