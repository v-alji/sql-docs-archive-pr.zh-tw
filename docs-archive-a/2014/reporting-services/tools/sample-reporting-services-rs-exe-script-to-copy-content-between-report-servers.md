---
title: 在報表伺服器之間遷移內容的範例 Reporting Services rs.exe 腳本 |Microsoft Docs
ms.custom: ''
ms.date: 07/27/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d81bb03a-a89e-4fc1-a62b-886fb5338150
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9dece153485e4c683df42a04b9301cf3a47c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699283"
---
# <a name="sample-reporting-services-rsexe-script-to-migrate-content-between-report-servers"></a><span data-ttu-id="0933a-102">在報表伺服器之間移轉內容的範例 Reporting Services rs.exe 指令碼</span><span class="sxs-lookup"><span data-stu-id="0933a-102">Sample Reporting Services rs.exe Script to Migrate Content between Report Servers</span></span>
  <span data-ttu-id="0933a-103">本主題包括並描述範例 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS 指令碼，該指令碼會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span><span class="sxs-lookup"><span data-stu-id="0933a-103">This topic includes and describes a sample [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS script that copies content items and settings from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span></span> <span data-ttu-id="0933a-104">不論是原生或 SharePoint 模式，RS.exe 都會和 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]一起安裝。</span><span class="sxs-lookup"><span data-stu-id="0933a-104">RS.exe is installed with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], both native and SharePoint mode.</span></span> <span data-ttu-id="0933a-105">這個指令碼會在伺服器之間複製 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 項目，例如報表和訂閱。</span><span class="sxs-lookup"><span data-stu-id="0933a-105">The script copies [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] items, for example reports and subscriptions, from server to another server.</span></span> <span data-ttu-id="0933a-106">這個指令碼同時支援 SharePoint 模式和原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-106">The script supports both SharePoint mode and Native mode report servers.</span></span>  
  
||  
|-|  
|<span data-ttu-id="0933a-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式</span><span class="sxs-lookup"><span data-stu-id="0933a-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
##  <a name="in-this-topic"></a><a name="bkmk_top"></a><span data-ttu-id="0933a-108">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="0933a-108">In this Topic:</span></span>  
  
-   [<span data-ttu-id="0933a-109">下載 ssrs_migration.rss 指令碼</span><span class="sxs-lookup"><span data-stu-id="0933a-109">To Download the ssrs_migration.rss Script</span></span>](#bkmk_download_script)  
  
-   [<span data-ttu-id="0933a-110">支援的案例</span><span class="sxs-lookup"><span data-stu-id="0933a-110">Supported Scenarios</span></span>](#bkmk_supported_scenarios)  
  
-   [<span data-ttu-id="0933a-111">指令碼移轉的項目及資源</span><span class="sxs-lookup"><span data-stu-id="0933a-111">Items and resources the script migrates</span></span>](#bkmk_what_is_migrated)  
  
-   [<span data-ttu-id="0933a-112">必要權限</span><span class="sxs-lookup"><span data-stu-id="0933a-112">Required Permissions</span></span>](#bkmk_required_permissions)  
  
-   [<span data-ttu-id="0933a-113">如何使用指令碼</span><span class="sxs-lookup"><span data-stu-id="0933a-113">How to use the script</span></span>](#bkmk_how_to_use_the_script)  
  
-   [<span data-ttu-id="0933a-114">參數描述</span><span class="sxs-lookup"><span data-stu-id="0933a-114">Parameter Description</span></span>](#bkmk_parameter_description)  
  
-   [<span data-ttu-id="0933a-115">更多範例</span><span class="sxs-lookup"><span data-stu-id="0933a-115">More Examples</span></span>](#bkmk_more_examples)  
  
    -   [<span data-ttu-id="0933a-116">原生模式報表伺服器到原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="0933a-116">Native Mode Report Server to Native Mode Report Server</span></span>](#bkmk_native_2_native)  
  
    -   [<span data-ttu-id="0933a-117">原生模式到 SharePoint 模式-根網站</span><span class="sxs-lookup"><span data-stu-id="0933a-117">Native Mode to SharePoint Mode - root site</span></span>](#bkmk_native_2_sharepoint_root)  
  
    -   [<span data-ttu-id="0933a-118">原生模式到 SharePoint 模式-' bi ' 網站集合</span><span class="sxs-lookup"><span data-stu-id="0933a-118">Native mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_native_2_sharepoint_with_site)  
  
    -   [<span data-ttu-id="0933a-119">SharePoint 模式到 SharePoint 模式-' bi ' 網站集合</span><span class="sxs-lookup"><span data-stu-id="0933a-119">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_sharepoint_2_sharepoint)  
  
    -   [<span data-ttu-id="0933a-120">原生模式到原生模式-Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="0933a-120">Native Mode to Native Mode - Azure Virtual Machine</span></span>](#bkmk_native_to_native_Azure_vm)  
  
    -   [<span data-ttu-id="0933a-121">SharePoint 模式-' bi ' 網站集合到 Azure 虛擬機器上的原生模式伺服器</span><span class="sxs-lookup"><span data-stu-id="0933a-121">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>](#bkmk_sharepoint_site_to_native_Azure_vm)  
  
-   [<span data-ttu-id="0933a-122">驗證</span><span class="sxs-lookup"><span data-stu-id="0933a-122">Verification</span></span>](#bkmk_verification)  
  
-   [<span data-ttu-id="0933a-123">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0933a-123">Troubleshooting</span></span>](#bkmk_troubleshoot)  
  
##  <a name="to-download-the-ssrs_migrationrss-script"></a><a name="bkmk_download_script"></a><span data-ttu-id="0933a-124">下載 ssrs_migration 的 rss 腳本</span><span class="sxs-lookup"><span data-stu-id="0933a-124">To Download the ssrs_migration.rss Script</span></span>  
 <span data-ttu-id="0933a-125">從 CodePlex 網站 [Reporting Services RS.exe script migrates content](https://azuresql.codeplex.com/releases/view/115207) (Reporting Services RS.exe 指令碼移轉內容) 下載指令碼至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-125">Download the script from the CodePlex site [Reporting Services RS.exe script migrates content](https://azuresql.codeplex.com/releases/view/115207) to a local folder.</span></span> <span data-ttu-id="0933a-126">請參閱本主題的 [如何使用指令碼](#bkmk_how_to_use_the_script) 一節，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0933a-126">See the section [How to use the script](#bkmk_how_to_use_the_script) in this topic for more information.</span></span>  
  
##  <a name="supported-scenarios"></a><a name="bkmk_supported_scenarios"></a><span data-ttu-id="0933a-127">支援的案例</span><span class="sxs-lookup"><span data-stu-id="0933a-127">Supported Scenarios</span></span>  
 <span data-ttu-id="0933a-128">這個指令碼同時支援 SharePoint 模式和原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-128">The script supports both SharePoint mode and Native mode report servers.</span></span> <span data-ttu-id="0933a-129">指令碼支援下列報表伺服器版本：</span><span class="sxs-lookup"><span data-stu-id="0933a-129">The script supports the following report server versions:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
 <span data-ttu-id="0933a-130">這個指令碼可用來在相同模式或不同模式的報表伺服器之間複製內容。</span><span class="sxs-lookup"><span data-stu-id="0933a-130">The script can be used to copy content between report servers of the same mode or different modes.</span></span> <span data-ttu-id="0933a-131">例如，您可以執行指令碼將內容從 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 原生模式報表伺服器複製到 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint 模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-131">For example, you can run the script to copy content from a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] native mode report server to a [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint mode report server.</span></span> <span data-ttu-id="0933a-132">您可以安裝 RS.exe 的任何伺服器執行這個指令碼。</span><span class="sxs-lookup"><span data-stu-id="0933a-132">You can run the script from any server where RS.exe is installed.</span></span> <span data-ttu-id="0933a-133">例如，在下列部署中，您可以：</span><span class="sxs-lookup"><span data-stu-id="0933a-133">For example, in the following deployment, you can:</span></span>  
  
-   <span data-ttu-id="0933a-134">在伺服器 A **上** 執行 RS.exe 和指令碼。</span><span class="sxs-lookup"><span data-stu-id="0933a-134">Run RS.exe and the script **ON** Server A.</span></span>  
  
-   <span data-ttu-id="0933a-135">**從** 伺服器 B 複製內容</span><span class="sxs-lookup"><span data-stu-id="0933a-135">To copy content **FROM** Server B</span></span>  
  
-   <span data-ttu-id="0933a-136">**到** 到伺服器 C</span><span class="sxs-lookup"><span data-stu-id="0933a-136">**TO** Server C</span></span>  
  
|<span data-ttu-id="0933a-137">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="0933a-137">Server name</span></span>|<span data-ttu-id="0933a-138">報表伺服器模式</span><span class="sxs-lookup"><span data-stu-id="0933a-138">Report Server Mode</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="0933a-139">伺服器 A</span><span class="sxs-lookup"><span data-stu-id="0933a-139">Server A</span></span>|<span data-ttu-id="0933a-140">原生</span><span class="sxs-lookup"><span data-stu-id="0933a-140">Native</span></span>|  
|<span data-ttu-id="0933a-141">伺服器 B</span><span class="sxs-lookup"><span data-stu-id="0933a-141">Server B</span></span>|<span data-ttu-id="0933a-142">SharePoint</span><span class="sxs-lookup"><span data-stu-id="0933a-142">SharePoint</span></span>|  
|<span data-ttu-id="0933a-143">伺服器 C</span><span class="sxs-lookup"><span data-stu-id="0933a-143">Server C</span></span>|<span data-ttu-id="0933a-144">SharePoint</span><span class="sxs-lookup"><span data-stu-id="0933a-144">SharePoint</span></span>|  
  
 <span data-ttu-id="0933a-145">如需 RS.exe 公用程式的詳細資訊，請參閱 [RS.exe 公用程式 &#40;SSRS&#41;](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0933a-145">For more information on the RS.exe utility, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
###  <a name="items-and-resources-the-script-migrates"></a><a name="bkmk_what_is_migrated"></a><span data-ttu-id="0933a-146">腳本所遷移的專案和資源</span><span class="sxs-lookup"><span data-stu-id="0933a-146">Items and resources the script migrates</span></span>  
 <span data-ttu-id="0933a-147">這個指令碼不會覆寫相同名稱的現有內容項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-147">The script will not write over existing content items of the same name.</span></span>  <span data-ttu-id="0933a-148">如果指令碼偵測到來源伺服器與目的地伺服器上有相同名稱的項目，則個別項目將會產生「失敗」訊息，但指令碼會繼續。</span><span class="sxs-lookup"><span data-stu-id="0933a-148">If the script detects items with the same name on the destination server that are on the source server, the individual items will result in a "failure" message and the script will continue.</span></span> <span data-ttu-id="0933a-149">下表列出指令碼可移轉至目標報表伺服器模式的內容和資源類型。</span><span class="sxs-lookup"><span data-stu-id="0933a-149">The following table lists the types of content and resources the script can migrate to target report server modes.</span></span>  
  
|<span data-ttu-id="0933a-150">項目</span><span class="sxs-lookup"><span data-stu-id="0933a-150">Item</span></span>|<span data-ttu-id="0933a-151">已移轉</span><span class="sxs-lookup"><span data-stu-id="0933a-151">Migrated</span></span>|<span data-ttu-id="0933a-152">SharePoint</span><span class="sxs-lookup"><span data-stu-id="0933a-152">SharePoint</span></span>|<span data-ttu-id="0933a-153">描述</span><span class="sxs-lookup"><span data-stu-id="0933a-153">Description</span></span>|  
|----------|--------------|----------------|-----------------|  
|<span data-ttu-id="0933a-154">密碼</span><span class="sxs-lookup"><span data-stu-id="0933a-154">Passwords</span></span>|<span data-ttu-id="0933a-155">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-155">**No**</span></span>|<span data-ttu-id="0933a-156">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-156">**No**</span></span>|<span data-ttu-id="0933a-157">密碼 **不會** 移轉。</span><span class="sxs-lookup"><span data-stu-id="0933a-157">Passwords are **NOT** migrated.</span></span> <span data-ttu-id="0933a-158">內容項目移轉之後，請更新目的地伺服器上的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="0933a-158">After content items are migrated, update the credential information on the destination server.</span></span> <span data-ttu-id="0933a-159">例如，具有預存認證的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0933a-159">For example, data sources with stored credentials.</span></span>|  
|<span data-ttu-id="0933a-160">我的報表</span><span class="sxs-lookup"><span data-stu-id="0933a-160">My Reports</span></span>|<span data-ttu-id="0933a-161">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-161">**No**</span></span>|<span data-ttu-id="0933a-162">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-162">**No**</span></span>|<span data-ttu-id="0933a-163">原生模式 [我的報表] 功能是以個別使用者登入為基礎，因此，除非使用 **-u** 參數執行 rss 指令碼，否則指令碼服務無法存取 [我的報表] 資料夾中使用者的內容。</span><span class="sxs-lookup"><span data-stu-id="0933a-163">The Native mode "My Reports" feature is based on individual user logins therefore the scripting service does not have access to content in "My Reports" folders for users other than the **-u** parameter used to run the rss script.</span></span> <span data-ttu-id="0933a-164">此外，"我的報表" 不是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sharepoint 模式的功能，而且資料夾中的專案無法複製到 sharepoint 環境。</span><span class="sxs-lookup"><span data-stu-id="0933a-164">Also, "My Reports" is not a feature of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode and items in the folders cannot be copied to a SharePoint environment.</span></span> <span data-ttu-id="0933a-165">因此，此腳本不會複製來源原生模式報表伺服器上 "我的報表" 資料夾中的報表專案。</span><span class="sxs-lookup"><span data-stu-id="0933a-165">Therefore, the script does not copy report items that are in the "My Reports" folders on a source native mode report server.</span></span> <span data-ttu-id="0933a-166">若要使用此腳本遷移 "我的報表" 資料夾中的內容，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0933a-166">To migrate the content in "My Reports" folders with this script, complete the following:</span></span><br /><br /> <span data-ttu-id="0933a-167">1) 在報表管理員中建立新的資料夾 (s) 。</span><span class="sxs-lookup"><span data-stu-id="0933a-167">1) Create new folder(s) in Report Manager.</span></span> <span data-ttu-id="0933a-168">或者，您可以為每位使用者建立資料夾或子資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-168">Optionally, you can create folders or subfolder for each user.</span></span><br /><br /> <span data-ttu-id="0933a-169">2) 以「我的報表」內容的其中一個使用者身分登入。</span><span class="sxs-lookup"><span data-stu-id="0933a-169">2) Login as one of the users with "My Reports" content.</span></span><br /><br /> <span data-ttu-id="0933a-170">3) 在報表管理員中，按一下 [**我的報表**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-170">3) In Report Manager, click the **My Reports** folder.</span></span><br /><br /> <span data-ttu-id="0933a-171">4) 按一下資料夾的**詳細資料**視圖。</span><span class="sxs-lookup"><span data-stu-id="0933a-171">4) Click the **Details** view for the folder.</span></span><br /><br /> <span data-ttu-id="0933a-172">5) 選取您要複製的每個報表。</span><span class="sxs-lookup"><span data-stu-id="0933a-172">5) Select each report that you want to copy.</span></span><br /><br /> <span data-ttu-id="0933a-173">6) 按一下 [報表管理員] 工具列中的 [**移動**]。</span><span class="sxs-lookup"><span data-stu-id="0933a-173">6) Click **Move** in the Report Manager toolbar.</span></span><br /><br /> <span data-ttu-id="0933a-174">7) 選取所需的目的地資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-174">7) Select the desired destination folder.</span></span><br /><br /> <span data-ttu-id="0933a-175">8) 針對每個使用者重複步驟2-7。</span><span class="sxs-lookup"><span data-stu-id="0933a-175">8) Repeat steps 2-7 for each user.</span></span><br /><br /> <span data-ttu-id="0933a-176">9) 執行腳本。</span><span class="sxs-lookup"><span data-stu-id="0933a-176">9) Run the script.</span></span>|  
|<span data-ttu-id="0933a-177">記錄</span><span class="sxs-lookup"><span data-stu-id="0933a-177">History</span></span>|<span data-ttu-id="0933a-178">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-178">**No**</span></span>|<span data-ttu-id="0933a-179">**否**</span><span class="sxs-lookup"><span data-stu-id="0933a-179">**No**</span></span>||  
|<span data-ttu-id="0933a-180">記錄設定</span><span class="sxs-lookup"><span data-stu-id="0933a-180">History settings</span></span>|<span data-ttu-id="0933a-181">是</span><span class="sxs-lookup"><span data-stu-id="0933a-181">Yes</span></span>|<span data-ttu-id="0933a-182">是</span><span class="sxs-lookup"><span data-stu-id="0933a-182">Yes</span></span>|<span data-ttu-id="0933a-183">雖然記錄設定會移轉，但是記錄詳細資料「不會」移轉。</span><span class="sxs-lookup"><span data-stu-id="0933a-183">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="0933a-184">排程</span><span class="sxs-lookup"><span data-stu-id="0933a-184">Schedules</span></span>|<span data-ttu-id="0933a-185">是</span><span class="sxs-lookup"><span data-stu-id="0933a-185">yes</span></span>|<span data-ttu-id="0933a-186">是</span><span class="sxs-lookup"><span data-stu-id="0933a-186">yes</span></span>|<span data-ttu-id="0933a-187">若要移轉排程，則必須在目標伺服器上執行 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="0933a-187">To migrate schedules, it is required that SQL Server Agent is running on the target server.</span></span> <span data-ttu-id="0933a-188">如果 SQL Server Agent 未在目標上執行，您將會看見類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0933a-188">If SQL Server Agent is not running on the target, you will see an error message similar to the following:</span></span><br /><br /> `Migrating schedules: 1 items found. Migrating schedule: theMondaySchedule ... FAILURE:  The SQL Agent service is not running. This operation requires the SQL Agent service. ---> Microsoft.ReportingServices.Diagnostics.Utilities.SchedulerNotResponding Exception: The SQL Agent service is not running. This operation requires the SQL Agent service.`|  
|<span data-ttu-id="0933a-189">角色和系統原則</span><span class="sxs-lookup"><span data-stu-id="0933a-189">Roles and system policies</span></span>|<span data-ttu-id="0933a-190">是</span><span class="sxs-lookup"><span data-stu-id="0933a-190">Yes</span></span>|<span data-ttu-id="0933a-191">是</span><span class="sxs-lookup"><span data-stu-id="0933a-191">Yes</span></span>|<span data-ttu-id="0933a-192">根據預設，指令碼不會在伺服器之間複製自訂的權限結構描述。</span><span class="sxs-lookup"><span data-stu-id="0933a-192">By default the script will not copy custom permission schema between servers.</span></span> <span data-ttu-id="0933a-193">預設行為是將專案複製到目的地伺服器，並將 [繼承父許可權] 旗標設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0933a-193">The default behavior is the items will be coied to the destination server with the 'inherit parent permissions' flag set to TRUE.</span></span> <span data-ttu-id="0933a-194">如果您希望指令碼複製個別項目的權限，請使用 SECURITY 參數。</span><span class="sxs-lookup"><span data-stu-id="0933a-194">If you want the script to copy permissions for individual items, use the SECURITY switch.</span></span><br /><br /> <span data-ttu-id="0933a-195">如果來源和目標伺服器**不屬於相同的報表伺服器模式** (例如從原生模式到 SharePoint 模式)，而且您使用 SECURITY 參數，則指令碼將會根據下列主題中的比較嘗試對應預設角色和群組：[將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="0933a-195">If the source and target servers are **not the same report server mode**, for example from native mode to SharePoint mode, and you use the SECURITY switch, the script will attempt to map default roles and groups based on the comparison in the following topic [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span> <span data-ttu-id="0933a-196">自訂角色和群組不會複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-196">Custom roles and groups are not copied to the destination server.</span></span><br /><br /> <span data-ttu-id="0933a-197">當指令碼在 **屬於相同模式**的伺服器之間進行複製，而且您使用 SECURITY 參數時，指令碼將會在目的地伺服器上建立新的角色 (原生模式) 或群組 (SharePoint 模式)。</span><span class="sxs-lookup"><span data-stu-id="0933a-197">When the script is copying between servers **that are the same mode**, and you use the SECURITY switch, the script will create new roles (native mode) or groups (SharePoint mode) on the destination server.</span></span><br /><br /> <span data-ttu-id="0933a-198">如果角色已出現在目的地伺服器上，指令碼將會建立類似下面的「失敗」訊息，並繼續移轉其他項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-198">If a role already exists on the destination server, the script will create a "Failure" message similar to the following, and continue migrating other items.</span></span> <span data-ttu-id="0933a-199">指令碼完成後，請確認目的地伺服器上的角色是否根據您的需求設定。</span><span class="sxs-lookup"><span data-stu-id="0933a-199">After the script completes, verify the roles on the destination server are configured to meet your needs.</span></span> <span data-ttu-id="0933a-200">移轉角色: 找到 8 個項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-200">the Migrating roles: 8 items found.</span></span><br /><br /> `Migrating role: Browser ... FAILURE: The role 'Browser' already exists and cannot be created. ---> Microsoft.ReportingServices.Diagnostics.Utilities.RoleAlreadyExistsException: The role 'Browser' already exists and cannot be created.`<br /><br /> <span data-ttu-id="0933a-201">如需詳細資訊，請參閱[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](../security/grant-user-access-to-a-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="0933a-201">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md)</span></span><br /><br /> <span data-ttu-id="0933a-202">**注意：** 如果來源伺服器上的使用者不存在於目的地伺服器上，指令碼就無法在目的地伺服器上套用角色指派，而且即使已使用 SECURITY 參數，也無法套用角色指派。</span><span class="sxs-lookup"><span data-stu-id="0933a-202">**Note:** if a user that exists on the source server does not exist on the destination server, the script cannot apply role assignments on the destination server, the script cannot apply role assignments, even if the SECURITY switch is used.</span></span>|  
|<span data-ttu-id="0933a-203">共用資料來源</span><span class="sxs-lookup"><span data-stu-id="0933a-203">Shared data source</span></span>|<span data-ttu-id="0933a-204">是</span><span class="sxs-lookup"><span data-stu-id="0933a-204">Yes</span></span>|<span data-ttu-id="0933a-205">是</span><span class="sxs-lookup"><span data-stu-id="0933a-205">Yes</span></span>|<span data-ttu-id="0933a-206">指令碼將不會覆寫目標伺服器上的現有項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-206">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="0933a-207">如果目標伺服器上已存在相同名稱的項目，您將會看見類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0933a-207">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating DataSource: /Data Sources/Aworks2012_oltp ... FAILURE:The item '/Data Sources/Aworks2012_oltp' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Data Source s/Aworks2012_oltp' already exists.`<br /><br /> <span data-ttu-id="0933a-208">認證 **不** 會複製作為資料來源的一部分。</span><span class="sxs-lookup"><span data-stu-id="0933a-208">Credentials are **NOT** copied over as part of the data source.</span></span> <span data-ttu-id="0933a-209">內容項目移轉之後，請更新目的地伺服器上的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="0933a-209">After content items are migrated, update the credential information on the destination server.</span></span>|  
|<span data-ttu-id="0933a-210">共用資料集</span><span class="sxs-lookup"><span data-stu-id="0933a-210">Shared dataset</span></span>|<span data-ttu-id="0933a-211">是</span><span class="sxs-lookup"><span data-stu-id="0933a-211">Yes</span></span>|<span data-ttu-id="0933a-212">是</span><span class="sxs-lookup"><span data-stu-id="0933a-212">Yes</span></span>||  
|<span data-ttu-id="0933a-213">資料夾</span><span class="sxs-lookup"><span data-stu-id="0933a-213">Folder</span></span>|<span data-ttu-id="0933a-214">是</span><span class="sxs-lookup"><span data-stu-id="0933a-214">Yes</span></span>|<span data-ttu-id="0933a-215">是</span><span class="sxs-lookup"><span data-stu-id="0933a-215">Yes</span></span>|<span data-ttu-id="0933a-216">指令碼將不會覆寫目標伺服器上的現有項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-216">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="0933a-217">如果目標伺服器上已存在相同名稱的項目，您將會看見類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0933a-217">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Folder: /Reports ... FAILURE: The item '/Reports' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports' already exists.`|  
|<span data-ttu-id="0933a-218">報告</span><span class="sxs-lookup"><span data-stu-id="0933a-218">Report</span></span>|<span data-ttu-id="0933a-219">是</span><span class="sxs-lookup"><span data-stu-id="0933a-219">Yes</span></span>|<span data-ttu-id="0933a-220">是</span><span class="sxs-lookup"><span data-stu-id="0933a-220">Yes</span></span>|<span data-ttu-id="0933a-221">指令碼將不會覆寫目標伺服器上的現有項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-221">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="0933a-222">如果目標伺服器上已存在相同名稱的項目，您將會看見類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0933a-222">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Report: /Reports/testThe item '/Reports/test' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports/test' already exists.`|  
|<span data-ttu-id="0933a-223">參數</span><span class="sxs-lookup"><span data-stu-id="0933a-223">Parameters</span></span>|<span data-ttu-id="0933a-224">是</span><span class="sxs-lookup"><span data-stu-id="0933a-224">Yes</span></span>|<span data-ttu-id="0933a-225">是</span><span class="sxs-lookup"><span data-stu-id="0933a-225">Yes</span></span>||  
|<span data-ttu-id="0933a-226">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="0933a-226">Subscriptions</span></span>|<span data-ttu-id="0933a-227">是</span><span class="sxs-lookup"><span data-stu-id="0933a-227">Yes</span></span>|<span data-ttu-id="0933a-228">是</span><span class="sxs-lookup"><span data-stu-id="0933a-228">Yes</span></span>||  
|<span data-ttu-id="0933a-229">記錄設定</span><span class="sxs-lookup"><span data-stu-id="0933a-229">History Settings</span></span>|<span data-ttu-id="0933a-230">是</span><span class="sxs-lookup"><span data-stu-id="0933a-230">Yes</span></span>|<span data-ttu-id="0933a-231">是</span><span class="sxs-lookup"><span data-stu-id="0933a-231">Yes</span></span>|<span data-ttu-id="0933a-232">雖然記錄設定會移轉，但是記錄詳細資料「不會」移轉。</span><span class="sxs-lookup"><span data-stu-id="0933a-232">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="0933a-233">處理選項</span><span class="sxs-lookup"><span data-stu-id="0933a-233">processing options</span></span>|<span data-ttu-id="0933a-234">是</span><span class="sxs-lookup"><span data-stu-id="0933a-234">Yes</span></span>|<span data-ttu-id="0933a-235">是</span><span class="sxs-lookup"><span data-stu-id="0933a-235">Yes</span></span>||  
|<span data-ttu-id="0933a-236">快取重新整理選項</span><span class="sxs-lookup"><span data-stu-id="0933a-236">cache refresh options</span></span>|<span data-ttu-id="0933a-237">是</span><span class="sxs-lookup"><span data-stu-id="0933a-237">Yes</span></span>|<span data-ttu-id="0933a-238">是</span><span class="sxs-lookup"><span data-stu-id="0933a-238">Yes</span></span>|<span data-ttu-id="0933a-239">相依設定會隨目錄項目一起移轉。</span><span class="sxs-lookup"><span data-stu-id="0933a-239">Dependent settings are migrated as part of a catalog item.</span></span> <span data-ttu-id="0933a-240">以下範例將示範指令碼移轉報表 (.rdl) 以及相關的設定 (例如快取重新整理選項)：</span><span class="sxs-lookup"><span data-stu-id="0933a-240">The following is the sample out of the script as it migrates a report (.rdl) and related settings such as cache refresh options:</span></span><br /><br /> <span data-ttu-id="0933a-241">移轉報表 TitleOnly.rdl 的參數: 找到 0 個項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-241">Migrating parameters for report TitleOnly.rdl 0 items found.</span></span><br /><br /> <span data-ttu-id="0933a-242">移轉報表 TitleOnly.rdl 的訂閱:找到 1 個項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-242">Migrating subscriptions for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="0933a-243">正在將訂用帳戶儲存在 \\ \server\public\savedreports 中做為 titleonly.rdl .。。SUCCESS</span><span class="sxs-lookup"><span data-stu-id="0933a-243">Migrating subscription Save in \\\server\public\savedreports as TitleOnly ... SUCCESS</span></span><br /><br /> <span data-ttu-id="0933a-244">移轉報表 TitleOnly.rdl 的記錄設定 …SUCCESS</span><span class="sxs-lookup"><span data-stu-id="0933a-244">Migrating history settings for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="0933a-245">移轉報表 TitleOnly.rdl 的處理選項 …找到 0 個項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-245">Migrating processing options for report TitleOnly.rdl ... 0 items found.</span></span><br /><br /> <span data-ttu-id="0933a-246">移轉報表 TitleOnly.rdl 的快取重新整理選項 …SUCCESS</span><span class="sxs-lookup"><span data-stu-id="0933a-246">Migrating cache refresh options for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="0933a-247">移轉報表 TitleOnly.rdl 的快取重新整理計劃:找到 1 個項目。</span><span class="sxs-lookup"><span data-stu-id="0933a-247">Migrating cache refresh plans for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="0933a-248">移轉快取重新整理計劃 titleonly_refresh735amM2F ...SUCCESS</span><span class="sxs-lookup"><span data-stu-id="0933a-248">Migrating cache refresh plan titleonly_refresh735amM2F ... SUCCESS</span></span>|  
|<span data-ttu-id="0933a-249">快取重新整理計劃</span><span class="sxs-lookup"><span data-stu-id="0933a-249">Cache refresh plans</span></span>|<span data-ttu-id="0933a-250">是</span><span class="sxs-lookup"><span data-stu-id="0933a-250">Yes</span></span>|<span data-ttu-id="0933a-251">是</span><span class="sxs-lookup"><span data-stu-id="0933a-251">Yes</span></span>||  
|<span data-ttu-id="0933a-252">影像</span><span class="sxs-lookup"><span data-stu-id="0933a-252">Images</span></span>|<span data-ttu-id="0933a-253">是</span><span class="sxs-lookup"><span data-stu-id="0933a-253">Yes</span></span>|<span data-ttu-id="0933a-254">是</span><span class="sxs-lookup"><span data-stu-id="0933a-254">Yes</span></span>||  
|<span data-ttu-id="0933a-255">報表組件</span><span class="sxs-lookup"><span data-stu-id="0933a-255">Report parts</span></span>|<span data-ttu-id="0933a-256">是</span><span class="sxs-lookup"><span data-stu-id="0933a-256">Yes</span></span>|<span data-ttu-id="0933a-257">是</span><span class="sxs-lookup"><span data-stu-id="0933a-257">Yes</span></span>||  
  
##  <a name="required-permissions"></a><a name="bkmk_required_permissions"></a> <span data-ttu-id="0933a-258">必要權限</span><span class="sxs-lookup"><span data-stu-id="0933a-258">Required Permissions</span></span>  
 <span data-ttu-id="0933a-259">指令碼中用來讀取或寫入項目和資源之所有方法所需的權限不盡相同。</span><span class="sxs-lookup"><span data-stu-id="0933a-259">The permissions required to read or write items and resources is not the same for all of the methods used in the script.</span></span> <span data-ttu-id="0933a-260">下表摘要列出每個項目或資源使用的方式，以及相關內容的連結。</span><span class="sxs-lookup"><span data-stu-id="0933a-260">The following table summarizes the methods used for each item or resource and links to related content.</span></span> <span data-ttu-id="0933a-261">請導覽至個別主題，查看必要的權限。</span><span class="sxs-lookup"><span data-stu-id="0933a-261">Navigate to the individual topic to see the required permissions.</span></span> <span data-ttu-id="0933a-262">例如，ListChildren 方法主題說明下列操作的必要權限：</span><span class="sxs-lookup"><span data-stu-id="0933a-262">For example the ListChildren method topic notes the required permissions of:</span></span>  
  
-   <span data-ttu-id="0933a-263">**原生模式的必要權限：** 項目的 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="0933a-263">**Native Mode Required Permissions:** ReadProperties on Item</span></span>  
  
-   <span data-ttu-id="0933a-264">**SharePoint 模式的必要權限：** ViewListItems</span><span class="sxs-lookup"><span data-stu-id="0933a-264">**SharePoint Mode Required Permissions:** ViewListItems</span></span>  
  
|<span data-ttu-id="0933a-265">項目或資源</span><span class="sxs-lookup"><span data-stu-id="0933a-265">Item or Resource</span></span>|<span data-ttu-id="0933a-266">來源</span><span class="sxs-lookup"><span data-stu-id="0933a-266">Source</span></span>|<span data-ttu-id="0933a-267">目標</span><span class="sxs-lookup"><span data-stu-id="0933a-267">Target</span></span>|  
|----------------------|------------|------------|  
|<span data-ttu-id="0933a-268">目錄項目</span><span class="sxs-lookup"><span data-stu-id="0933a-268">Catalog items</span></span>|<xref:ReportService2010.ReportingService2010.ListChildren%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemLink%2A>|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.SetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataSource%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateLinkedItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateFolder%2A>|  
|<span data-ttu-id="0933a-269">角色</span><span class="sxs-lookup"><span data-stu-id="0933a-269">Role</span></span>|<xref:ReportService2010.ReportingService2010.ListRoles%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|  
|<span data-ttu-id="0933a-270">系統原則</span><span class="sxs-lookup"><span data-stu-id="0933a-270">System Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|  
|<span data-ttu-id="0933a-271">排程</span><span class="sxs-lookup"><span data-stu-id="0933a-271">Schedule</span></span>|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|  
|<span data-ttu-id="0933a-272">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="0933a-272">Subscription</span></span>|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|  
|<span data-ttu-id="0933a-273">快取重新整理計劃</span><span class="sxs-lookup"><span data-stu-id="0933a-273">Cache refresh plan</span></span>|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|  
|<span data-ttu-id="0933a-274">參數</span><span class="sxs-lookup"><span data-stu-id="0933a-274">Parameters</span></span>|<xref:ReportService2010.ReportingService2010.GetItemParameters%2A>|<xref:ReportService2010.ReportingService2010.SetItemParameters%2A>|  
|<span data-ttu-id="0933a-275">執行選項</span><span class="sxs-lookup"><span data-stu-id="0933a-275">Execution options</span></span>|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|  
|<span data-ttu-id="0933a-276">快取選項</span><span class="sxs-lookup"><span data-stu-id="0933a-276">Cache options</span></span>|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|  
|<span data-ttu-id="0933a-277">記錄設定</span><span class="sxs-lookup"><span data-stu-id="0933a-277">History settings</span></span>|<xref:ReportService2010.ReportingService2010.GetItemHistoryOptions%2A>|<xref:ReportService2010.ReportingService2010.SetItemHistoryOptions%2A>|  
|<span data-ttu-id="0933a-278">項目原則</span><span class="sxs-lookup"><span data-stu-id="0933a-278">Item Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|  
  
 <span data-ttu-id="0933a-279">如需詳細資訊，請參閱 [將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="0933a-279">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>  
  
##  <a name="how-to-use-the-script"></a><a name="bkmk_how_to_use_the_script"></a><span data-ttu-id="0933a-280">如何使用腳本</span><span class="sxs-lookup"><span data-stu-id="0933a-280">How to use the script</span></span>  
  
1.  <span data-ttu-id="0933a-281">將指令碼檔案下載至本機資料夾，例如 **c:\rss\ssrs_migration.rss**。</span><span class="sxs-lookup"><span data-stu-id="0933a-281">Download the script file to a local folder, for example **c:\rss\ssrs_migration.rss**.</span></span>  
  
2.  <span data-ttu-id="0933a-282">**以系統管理許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="0933a-282">Open a command prompt **with administrative privileges**.</span></span>  
  
3.  <span data-ttu-id="0933a-283">導覽至包含 ssrs_migration.rss 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-283">Navigate to the folder containing the ssrs_migration.rss file.</span></span>  
  
4.  <span data-ttu-id="0933a-284">搭配適合您狀況的參數執行命令。</span><span class="sxs-lookup"><span data-stu-id="0933a-284">Run the command with the parameters appropriate for your scenario.</span></span>  
  
 <span data-ttu-id="0933a-285">**基本範例，原生模式報表伺服器到原生模式報表伺服器：**</span><span class="sxs-lookup"><span data-stu-id="0933a-285">**Basic Example, native mode report server to native mode report server:**</span></span>  
  
 <span data-ttu-id="0933a-286">下列範例將從原生模式 **Sourceserver** 將內容移轉至原生模式 **Targetserver**。</span><span class="sxs-lookup"><span data-stu-id="0933a-286">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
 ```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"
```
  
 <span data-ttu-id="0933a-287">**使用注意事項：**</span><span class="sxs-lookup"><span data-stu-id="0933a-287">**Usage notes:**</span></span>  
  
-   <span data-ttu-id="0933a-288">指令碼會以兩個步驟執行。</span><span class="sxs-lookup"><span data-stu-id="0933a-288">The script runs in two steps.</span></span>  
  
     <span data-ttu-id="0933a-289">第一個步驟是稽核，傳回將要移轉的項目清單，第二個步驟則是移轉程序。</span><span class="sxs-lookup"><span data-stu-id="0933a-289">The first step is an audit, to return a list of items that will be migrated and the second step is the migration process.</span></span>  
  
     <span data-ttu-id="0933a-290">如果您只是想查看可能的移轉清單，或是想要修改參數，可以 **在第一個步驟之後取消指令碼** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-290">You can **cancel the script after step** one if you only want to see the possible migration list or you want to modify the parameters.</span></span> <span data-ttu-id="0933a-291">第一個步驟中不會列出相依設定。</span><span class="sxs-lookup"><span data-stu-id="0933a-291">Dependent settings are not listed in step one.</span></span> <span data-ttu-id="0933a-292">例如，報表的快取選項不會列出，而是列出報表本身。</span><span class="sxs-lookup"><span data-stu-id="0933a-292">For example, the cache options of a report are not listed but the report itself is.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="0933a-293">若您只想稽核單一伺服器，請為來源和目的地使用相同的伺服器，然後在完成步驟 1 後取消使用。</span><span class="sxs-lookup"><span data-stu-id="0933a-293">If you want to just audit a single server, use the same server for source and destination and cancel after step 1</span></span>  
  
     <span data-ttu-id="0933a-294">步驟 1 稽核資訊相當適合用於檢閱來源和目標原生模式伺服器上的現有角色。</span><span class="sxs-lookup"><span data-stu-id="0933a-294">A good use of the step 1 audit information is to review existing roles on both the source and target Native mode server.</span></span> <span data-ttu-id="0933a-295">以下是步驟一稽核清單的範例。</span><span class="sxs-lookup"><span data-stu-id="0933a-295">The following is an example of the step one audit list.</span></span> <span data-ttu-id="0933a-296">請注意清單中包含一個 [角色] 區段，因為使用了 switch-v security="True" 參數：</span><span class="sxs-lookup"><span data-stu-id="0933a-296">Notice the list includes a "roles" section because the switch-v security="True" was used:</span></span>  
  
    -   `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: Model Item Browser`  
  
         `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: CustomRole`  
  
         `Role: Model Item Browser`  
  
         `Role: My Reports`  
  
         `Role: Publisher`  
  
         `Role: Report Builder`  
  
         `Role: System Administrator`  
  
         `Role: System User`  
  
         `Retrieving system policies:`  
  
         `Retrieving system policies:`  
  
         `System policy: BUILTIN\Administrators`  
  
         `System policy: domain\user1`  
  
         `System policy: domain\ueser2`  
  
         `Retrieving schedules:`  
  
         `Schedule: theMondaySchedule`  
  
         `Retrieving catalog items. This may take a while.`  
  
         `Folder: /Data Sources`  
  
         `DataSource: /Data Sources/Aworks2012_oltp`  
  
         `Folder: /images`  
  
         `Resource: /images/Boba Fett.png`  
  
         `Resource: /images/R2-D2.png`  
  
         `Folder: /Reports`  
  
         `Report: /Reports/products`  
  
         `Report: /Reports/test`  
  
         `Report: /Reports/TitleOnly`  
  
-   <span data-ttu-id="0933a-297">SOURCE_URL 和 TARGET_URL 必須是指向來源和目標 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 報表伺服器的有效報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="0933a-297">The SOURCE_URL and TARGET_URL must be valid report server URLs that point to the source and target [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="0933a-298">在原生模式中，報表伺服器 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="0933a-298">In native mode, a report server URL looks like the following:</span></span>  
  
    -   `http://servername/reportserver`  
  
     <span data-ttu-id="0933a-299">在 SharePoint 模式中，URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="0933a-299">In SharePoint mode the URL looks like the following:</span></span>  
  
    -   `http://servername/_vti_bin/reportserver`  
  
-   <span data-ttu-id="0933a-300">在 SharePoint 中對使用者呈現的虛擬資料夾結構可能與基礎結構有所不同。</span><span class="sxs-lookup"><span data-stu-id="0933a-300">The virtual folder structure presented to the user in SharePoint might be different than the underlying one.</span></span> <span data-ttu-id="0933a-301">在瀏覽器中開啟 `http://servername/_vti_bin/reportserver` 或 `http://servername/sites/site_name/_vti_bin/reportserver` ，查看非虛擬資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="0933a-301">Open `http://servername/_vti_bin/reportserver` or `http://servername/sites/site_name/_vti_bin/reportserver` in a browser to see the non-virtual folder structure.</span></span> <span data-ttu-id="0933a-302">這樣有助於在 SharePoint 模式中，為伺服器設定 "/" 以外的來源資料夾和目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-302">This is helpful for setting source folder and target folder to something other than "/", for a server in SharePoint mode.</span></span>  
  
-   <span data-ttu-id="0933a-303">密碼不會移轉，而且必須重新輸入，例如具有預存認證的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0933a-303">Passwords are not migrated, and must be re-entered, for example data sources with stored credentials.</span></span>  
  
##  <a name="parameter-description"></a><a name="bkmk_parameter_description"></a><span data-ttu-id="0933a-304">參數描述</span><span class="sxs-lookup"><span data-stu-id="0933a-304">Parameter Description</span></span>  
  
|<span data-ttu-id="0933a-305">參數</span><span class="sxs-lookup"><span data-stu-id="0933a-305">Parameter</span></span>|<span data-ttu-id="0933a-306">描述</span><span class="sxs-lookup"><span data-stu-id="0933a-306">Description</span></span>|<span data-ttu-id="0933a-307">必要</span><span class="sxs-lookup"><span data-stu-id="0933a-307">Required</span></span>|  
|---------------|-----------------|--------------|  
|<span data-ttu-id="0933a-308">**-s** Source_URL</span><span class="sxs-lookup"><span data-stu-id="0933a-308">**-s** Source_URL</span></span>|<span data-ttu-id="0933a-309">來源報表伺服器的 URL</span><span class="sxs-lookup"><span data-stu-id="0933a-309">URL of the source report server</span></span>|<span data-ttu-id="0933a-310">是</span><span class="sxs-lookup"><span data-stu-id="0933a-310">Yes</span></span>|  
|<span data-ttu-id="0933a-311">**-u** Domain\password **-p** password</span><span class="sxs-lookup"><span data-stu-id="0933a-311">**-u** Domain\password **-p** password</span></span>|<span data-ttu-id="0933a-312">來源伺服器的認證。</span><span class="sxs-lookup"><span data-stu-id="0933a-312">Credentials for source server.</span></span>|<span data-ttu-id="0933a-313">(選擇性) 如果遺失則使用預設認證</span><span class="sxs-lookup"><span data-stu-id="0933a-313">OPTIONAL, default credentials are used if missing</span></span>|  
|<span data-ttu-id="0933a-314">**-v st**="SITE"</span><span class="sxs-lookup"><span data-stu-id="0933a-314">**-v st**="SITE"</span></span>||<span data-ttu-id="0933a-315">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0933a-315">OPTIONAL.</span></span> <span data-ttu-id="0933a-316">這個參數僅用於 SharePoint 模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-316">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="0933a-317">**- v f**="SOURCEFOLDER"</span><span class="sxs-lookup"><span data-stu-id="0933a-317">**- v f**="SOURCEFOLDER"</span></span>|<span data-ttu-id="0933a-318">設定為 "/" 表示移轉所有內容，設定為類似 "/folder/subfolder" 則表示部分移轉。</span><span class="sxs-lookup"><span data-stu-id="0933a-318">Set to "/" for migrating everything, or to something like "/folder/subfolder" for partial migration.</span></span> <span data-ttu-id="0933a-319">將會複製這個資料夾中的所有內容</span><span class="sxs-lookup"><span data-stu-id="0933a-319">Everything within this folder will be copied</span></span>|<span data-ttu-id="0933a-320">(選擇性) 預設值為 "/"。</span><span class="sxs-lookup"><span data-stu-id="0933a-320">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="0933a-321">**-v ts**="TARGET_URL"</span><span class="sxs-lookup"><span data-stu-id="0933a-321">**-v ts**="TARGET_URL"</span></span>|<span data-ttu-id="0933a-322">目標 RS 伺服器的 URL</span><span class="sxs-lookup"><span data-stu-id="0933a-322">'URL of the target RS server"</span></span>||  
|<span data-ttu-id="0933a-323">**-v tu**="domain\username" **-v tp**="password"</span><span class="sxs-lookup"><span data-stu-id="0933a-323">**-v tu**="domain\username" **-v tp**="password"</span></span>|<span data-ttu-id="0933a-324">目標伺服器的認證。</span><span class="sxs-lookup"><span data-stu-id="0933a-324">'Credentials for target server.</span></span>|<span data-ttu-id="0933a-325">(選擇性) 如果遺失則使用預設認證。</span><span class="sxs-lookup"><span data-stu-id="0933a-325">OPTIONAL, default credentials are used if missing.</span></span> <span data-ttu-id="0933a-326">**注意：** 在目標伺服器中，使用者將列為共用排程的「建立者」，以及報表項目的「修改者」帳戶。</span><span class="sxs-lookup"><span data-stu-id="0933a-326">**Note:** the user will be listed as the "creator" of shared schedules and "modified by" account for report items, in the target server.</span></span>|  
|<span data-ttu-id="0933a-327">**-v tst**="SITE"</span><span class="sxs-lookup"><span data-stu-id="0933a-327">**-v tst**="SITE"</span></span>||<span data-ttu-id="0933a-328">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0933a-328">OPTIONAL.</span></span> <span data-ttu-id="0933a-329">這個參數僅用於 SharePoint 模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-329">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="0933a-330">**-v tf** ="TARGETFOLDER"</span><span class="sxs-lookup"><span data-stu-id="0933a-330">**-v tf** ="TARGETFOLDER"</span></span>|<span data-ttu-id="0933a-331">設定為 "/" 表示移轉至根層級。</span><span class="sxs-lookup"><span data-stu-id="0933a-331">'Set to "/" for migrating into the root level.</span></span> <span data-ttu-id="0933a-332">設定為 "/folder/subfolder" 表示複製到已存在的位置。</span><span class="sxs-lookup"><span data-stu-id="0933a-332">Set to "/folder/subfolder" to copy into a that already exists.</span></span> <span data-ttu-id="0933a-333">"SOURCEFOLDER" 內的所有內容都會複製到 "TARGETFOLDER"。</span><span class="sxs-lookup"><span data-stu-id="0933a-333">Everything within "SOURCEFOLDER" will be copied into "TARGETFOLDER.</span></span>|<span data-ttu-id="0933a-334">(選擇性) 預設值為 "/"。</span><span class="sxs-lookup"><span data-stu-id="0933a-334">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="0933a-335">**-v security**= "True/False"</span><span class="sxs-lookup"><span data-stu-id="0933a-335">**-v security**= "True/False"</span></span>|<span data-ttu-id="0933a-336">如果設為 "False"，則目的地目錄項目將會根據目標系統的設定繼承安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0933a-336">If set to "False", destination catalog items will inherit security setting according to the settings of the target system.</span></span> <span data-ttu-id="0933a-337">這是在不同報表伺服器類型 (例如，原生模式到 SharePoint 模式) 之間進行移轉的建議設定。</span><span class="sxs-lookup"><span data-stu-id="0933a-337">This is the recommended setting for migrations between different report server types, for example native mode to SharePoint mode.</span></span> <span data-ttu-id="0933a-338">如果設為 "True"，則指令碼會嘗試移轉安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0933a-338">If set to "True", the script attempts to migrate security settings.</span></span>|<span data-ttu-id="0933a-339">(選擇性) 預設值為 "False"。</span><span class="sxs-lookup"><span data-stu-id="0933a-339">OPTIONAL, default is "False".</span></span>|  
  
##  <a name="more-examples"></a><a name="bkmk_more_examples"></a><span data-ttu-id="0933a-340">更多範例</span><span class="sxs-lookup"><span data-stu-id="0933a-340">More Examples</span></span>  
  
###  <a name="native-mode-report-server-to-native-mode-report-server"></a><a name="bkmk_native_2_native"></a><span data-ttu-id="0933a-341">原生模式報表伺服器到原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="0933a-341">Native Mode Report Server to Native Mode Report Server</span></span>  
 <span data-ttu-id="0933a-342">下列範例將從原生模式 **Sourceserver** 將內容移轉至原生模式 **Targetserver**。</span><span class="sxs-lookup"><span data-stu-id="0933a-342">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"  
```  
  
 <span data-ttu-id="0933a-343">下列範例將會加入安全性參數：</span><span class="sxs-lookup"><span data-stu-id="0933a-343">The following example adds the security switch:</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password" -v security="True"  
```  
  
###  <a name="native-mode-to-sharepoint-mode---root-site"></a><a name="bkmk_native_2_sharepoint_root"></a> <span data-ttu-id="0933a-344">原生模式到 SharePoint 模式 - 根網站</span><span class="sxs-lookup"><span data-stu-id="0933a-344">Native Mode to SharePoint Mode - root site</span></span>  
 <span data-ttu-id="0933a-345">下列範例將從原生模式 **SourceServer** 將內容移轉至 SharePoint 模式伺服器 **TargetServer** 上的「根網站」。</span><span class="sxs-lookup"><span data-stu-id="0933a-345">The following example migrates content from a native mode **SourceServer** to the "root site " on a SharePoint mode server **TargetServer**.</span></span> <span data-ttu-id="0933a-346">原生模式伺服器上的 [報表] 和 [資料來源] 資料夾移轉後成為 SharePoint 部署上的新文件庫。</span><span class="sxs-lookup"><span data-stu-id="0933a-346">The "Reports" and "Data Sources" folders on the native mode server as migrated as new libraries on the SharePoint deployment.</span></span>  
  
 <span data-ttu-id="0933a-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span><span class="sxs-lookup"><span data-stu-id="0933a-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/_vti_bin/ReportServer" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_native_2_sharepoint_with_site"></a><span data-ttu-id="0933a-348">原生模式到 SharePoint 模式-' bi ' 網站集合</span><span class="sxs-lookup"><span data-stu-id="0933a-348">Native mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="0933a-349">下列範例將從原生模式伺服器將內容移轉至包含網站集合 "sites/bi" 和共用文件庫的 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-349">The following example migrates content from a native mode server to a SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span> <span data-ttu-id="0933a-350">指令碼會在目的地文件庫中建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-350">The script creates folders in document the destination library.</span></span> <span data-ttu-id="0933a-351">例如，指令碼將在目標文件庫中建立 [報表] 和 [資料來源] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0933a-351">For example, the script will create a "Reports" and "Data Sources" folders in the target document library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="sharepoint-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_sharepoint_2_sharepoint"></a><span data-ttu-id="0933a-352">SharePoint 模式到 SharePoint 模式-' bi ' 網站集合</span><span class="sxs-lookup"><span data-stu-id="0933a-352">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="0933a-353">下列範例會移轉內容：</span><span class="sxs-lookup"><span data-stu-id="0933a-353">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="0933a-354">從包含 "sites/bi" 網站集合和共用文件庫的 SharePoint 伺服器 **SourceServer** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-354">From a SharePoint server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="0933a-355">到包含 "sites/bi" 網站集合和共用文件庫的 **TargetServer** SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-355">To a **TargetServer** SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/_vti_bin/reportserver -v st="sites/bi" -v f="Shared Documents" -u Domain\User1 -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-native-mode---azure-virtual-machine"></a><a name="bkmk_native_to_native_Azure_vm"></a><span data-ttu-id="0933a-356">原生模式到原生模式-Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="0933a-356">Native Mode to Native Mode - Azure Virtual Machine</span></span>  
 <span data-ttu-id="0933a-357">下列範例會移轉內容：</span><span class="sxs-lookup"><span data-stu-id="0933a-357">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="0933a-358">從原生模式報表伺服器 **SourceServer**。</span><span class="sxs-lookup"><span data-stu-id="0933a-358">From a Native mode report server **SourceServer**.</span></span>  
  
-   <span data-ttu-id="0933a-359">到 Azure 虛擬機器上執行的 **TargetServer** 原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-359">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="0933a-360">**TargetServer**不會聯結至**SourceServer**的網域，而人員**則是 Azure**虛擬機器**TargetServer**上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0933a-360">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Password2"  
```  
  
> [!TIP]  
>  <span data-ttu-id="0933a-361">如需如何使用 Windows PowerShell 在 Windows Azure 虛擬機器上建立 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 報表伺服器的詳細資訊，請參閱[使用 PowerShell 建立具有原生模式報表伺服器的 Azure VM](https://msdn.microsoft.com/library/dn449661.aspx) \(不分機器翻譯\)。</span><span class="sxs-lookup"><span data-stu-id="0933a-361">For information on how to use Windows PowerShell to create [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report servers on Azure virtual machines, see [Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/dn449661.aspx).</span></span>  
  
##  <a name="sharepoint-mode--bi-site-collection-to-a-native-mode-server-on-azure-virtual-machine"></a><a name="bkmk_sharepoint_site_to_native_Azure_vm"></a><span data-ttu-id="0933a-362">SharePoint 模式-' bi ' 網站集合到 Azure 虛擬機器上的原生模式伺服器</span><span class="sxs-lookup"><span data-stu-id="0933a-362">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>  
 <span data-ttu-id="0933a-363">下列範例會移轉內容：</span><span class="sxs-lookup"><span data-stu-id="0933a-363">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="0933a-364">從包含 "sites/bi" 網站集合和共用文件庫的 SharePoint 模式報表伺服器 **SourceServer** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-364">From a SharePoint mode report server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="0933a-365">到 Azure 虛擬機器上執行的 **TargetServer** 原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-365">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="0933a-366">**TargetServer**不會聯結至**SourceServer**的網域，而人員**則是 Azure**虛擬機器**TargetServer**上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0933a-366">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://uetesta02/_vti_bin/reportserver -u user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Passowrd2"  
```  
  
##  <a name="verification"></a><a name="bkmk_verification"></a><span data-ttu-id="0933a-367">驗證</span><span class="sxs-lookup"><span data-stu-id="0933a-367">Verification</span></span>  
 <span data-ttu-id="0933a-368">本節摘要說明在目的地伺服器上驗證內容和原則是否成功移轉所採取的一些步驟。</span><span class="sxs-lookup"><span data-stu-id="0933a-368">The section summarizes some of the steps to take on the destination server to verify content and policies were successfully migrated.</span></span>  
  
### <a name="schedules"></a><span data-ttu-id="0933a-369">排程</span><span class="sxs-lookup"><span data-stu-id="0933a-369">Schedules</span></span>  
 <span data-ttu-id="0933a-370">若要驗證目標伺服器上的排程：</span><span class="sxs-lookup"><span data-stu-id="0933a-370">To verify schedules on the target server:</span></span>  
  
 <span data-ttu-id="0933a-371">**原生模式**</span><span class="sxs-lookup"><span data-stu-id="0933a-371">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="0933a-372">瀏覽至目的地伺服器上的報表管理員。</span><span class="sxs-lookup"><span data-stu-id="0933a-372">Browse to Report Manager on the destination server.</span></span>  
  
2.  <span data-ttu-id="0933a-373">按一下上層功能表上的 **[網站設定]** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-373">Click **Site Settings** on the top menu.</span></span>  
  
3.  <span data-ttu-id="0933a-374">按一下左窗格中的 **[排程]** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-374">Click **Schedules** in the left pane.</span></span>  
  
 <span data-ttu-id="0933a-375">**SharePoint 模式：**</span><span class="sxs-lookup"><span data-stu-id="0933a-375">**SharePoint Mode:**</span></span>  
  
1.  <span data-ttu-id="0933a-376">瀏覽至 **[網站設定]**。</span><span class="sxs-lookup"><span data-stu-id="0933a-376">Browse to **Site settings**.</span></span>  
  
2.  <span data-ttu-id="0933a-377">在 **[Reporting Services]** 群組中，按一下 **[管理共用排程]**。</span><span class="sxs-lookup"><span data-stu-id="0933a-377">In the **Reporting Services** group, click **Manage Shared Schedules**.</span></span>  
  
### <a name="roles-and-groups"></a><span data-ttu-id="0933a-378">角色和群組</span><span class="sxs-lookup"><span data-stu-id="0933a-378">Roles and Groups</span></span>  
 <span data-ttu-id="0933a-379">**原生模式**</span><span class="sxs-lookup"><span data-stu-id="0933a-379">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="0933a-380">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您的原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0933a-380">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to your native mode report server.</span></span>  
  
2.  <span data-ttu-id="0933a-381">在**物件總管**按一下 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="0933a-381">In **Object Explorer** click **Security**.</span></span>  
  
3.  <span data-ttu-id="0933a-382">按一下 [角色]  。</span><span class="sxs-lookup"><span data-stu-id="0933a-382">Click **Roles**.</span></span>  
  
##  <a name="troubleshooting"></a><a name="bkmk_troubleshoot"></a> <span data-ttu-id="0933a-383">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0933a-383">Troubleshooting</span></span>  
 <span data-ttu-id="0933a-384">使用追蹤旗標 **-t** 取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0933a-384">Use the trace flag **-t** to receive more information.</span></span> <span data-ttu-id="0933a-385">例如，如果您執行指令碼並且看到類似下面的訊息</span><span class="sxs-lookup"><span data-stu-id="0933a-385">For example, if you run the script and see a message similar to the following</span></span>  
  
-   <span data-ttu-id="0933a-386">無法連接到伺服器： HTTP:// \<servername> /ReportServer/ReportService2010.asmx</span><span class="sxs-lookup"><span data-stu-id="0933a-386">Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx</span></span>  
  
 <span data-ttu-id="0933a-387">使用 **-t**旗標再次執行腳本，以查看類似下列的訊息：</span><span class="sxs-lookup"><span data-stu-id="0933a-387">Run the script again with the **-t** flag, to see a message similar to the following:</span></span>  
  
-   <span data-ttu-id="0933a-388">System.exception：無法連接到伺服器： HTTP:// \<servername> /ReportServer/ReportService2010.asmx---> 系統 .net。 WebException：**要求失敗，HTTP 狀態為401：未經授權**。</span><span class="sxs-lookup"><span data-stu-id="0933a-388">System.Exception: Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx ---> System.Net.WebException: **The request failed with HTTP status 401: Unauthorized**.</span></span>   <span data-ttu-id="0933a-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)   at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)   at Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired()   at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService(String url, String userName, String password, String domain, Int32 timeout)   at Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()   --- 內部例外狀況堆疊追蹤結束 ---</span><span class="sxs-lookup"><span data-stu-id="0933a-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)   at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)   at Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired()   at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService(String url, String userName, String password, String domain, Int32 timeout)   at Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()   --- End of inner exception stack trace ---</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0933a-390">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0933a-390">See Also</span></span>  
 <span data-ttu-id="0933a-391">[RS.exe 公用程式 &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0933a-391">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span></span>  
 [<span data-ttu-id="0933a-392">將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較</span><span class="sxs-lookup"><span data-stu-id="0933a-392">Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions</span></span>](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
