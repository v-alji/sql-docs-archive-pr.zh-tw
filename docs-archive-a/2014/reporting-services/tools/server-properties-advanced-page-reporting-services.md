---
title: 伺服器屬性 (進階頁面) - Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1834b1eb458ec718db23ad229a4ed6e04ae826c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597017"
---
# <a name="server-properties-advanced-page---reporting-services"></a><span data-ttu-id="23ab5-102">伺服器屬性 (進階頁面) - Reporting Services</span><span class="sxs-lookup"><span data-stu-id="23ab5-102">Server Properties (Advanced Page) - Reporting Services</span></span>
  <span data-ttu-id="23ab5-103">您可以使用這個頁面來設定報表伺服器的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="23ab5-103">Use this page to set system properties on the report server.</span></span> <span data-ttu-id="23ab5-104">有許多方式可設定系統屬性。</span><span class="sxs-lookup"><span data-stu-id="23ab5-104">There are a number of ways to set system properties.</span></span> <span data-ttu-id="23ab5-105">這項工具提供了圖形化使用者介面，如此您不需要撰寫程式碼就可以設定屬性。</span><span class="sxs-lookup"><span data-stu-id="23ab5-105">This tool provides a graphical user interface so that you can set properties without having to write code.</span></span>  
  
 <span data-ttu-id="23ab5-106">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連接至報表伺服器執行個體、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23ab5-106">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="23ab5-107">按一下 **[進階]** ，即可開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="23ab5-107">Click **Advanced** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23ab5-108">選項。</span><span class="sxs-lookup"><span data-stu-id="23ab5-108">Options</span></span>  
 <span data-ttu-id="23ab5-109">**EnableMyReports**</span><span class="sxs-lookup"><span data-stu-id="23ab5-109">**EnableMyReports**</span></span>  
 <span data-ttu-id="23ab5-110">指出 [我的報表] 功能是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="23ab5-110">Indicates whether the My Reports feature is enabled.</span></span> <span data-ttu-id="23ab5-111">值若為 `true` 表示此功能已啟用。</span><span class="sxs-lookup"><span data-stu-id="23ab5-111">A value of `true` indicates that the feature is enabled.</span></span>  
  
 <span data-ttu-id="23ab5-112">**MyReportsRole**</span><span class="sxs-lookup"><span data-stu-id="23ab5-112">**MyReportsRole**</span></span>  
 <span data-ttu-id="23ab5-113">在使用者之 [我的報表] 資料夾上建立安全性原則時所使用的角色名稱。</span><span class="sxs-lookup"><span data-stu-id="23ab5-113">The name of the role used when creating security policies on user's My Reports folders.</span></span> <span data-ttu-id="23ab5-114">預設值是 `My Reports Role`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-114">The default value is `My Reports Role`.</span></span>  
  
 <span data-ttu-id="23ab5-115">**EnableClientPrinting**</span><span class="sxs-lookup"><span data-stu-id="23ab5-115">**EnableClientPrinting**</span></span>  
 <span data-ttu-id="23ab5-116">決定是否可從報表伺服器下載 RSClientPrint ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="23ab5-116">Determines whether the RSClientPrint ActiveX control is available for download from the report server.</span></span> <span data-ttu-id="23ab5-117">有效值為 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-117">The valid values are `true` and `false`.</span></span> <span data-ttu-id="23ab5-118">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-118">The default value is `true`.</span></span> <span data-ttu-id="23ab5-119">如需此控制項所需之其他設定的詳細資訊，請參閱 [啟用和停用 Reporting Services 的用戶端列印功能](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-119">For more information about additional settings that are required for this control, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
 <span data-ttu-id="23ab5-120">**EnableExecutionLogging**</span><span class="sxs-lookup"><span data-stu-id="23ab5-120">**EnableExecutionLogging**</span></span>  
 <span data-ttu-id="23ab5-121">指出報表執行記錄是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="23ab5-121">Indicates whether report execution logging is enabled.</span></span> <span data-ttu-id="23ab5-122">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-122">The default value is `true`.</span></span> <span data-ttu-id="23ab5-123">如需報表伺服器執行記錄的詳細資訊，請參閱[報表伺服器執行記錄和 ExecutionLog3 視圖](../report-server/report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-123">For more information about the report server execution log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="23ab5-124">**ExecutionLogDaysKept**</span><span class="sxs-lookup"><span data-stu-id="23ab5-124">**ExecutionLogDaysKept**</span></span>  
 <span data-ttu-id="23ab5-125">要將報表執行資訊保留在執行記錄中的天數。</span><span class="sxs-lookup"><span data-stu-id="23ab5-125">The number of days to keep report execution information in the execution log.</span></span> <span data-ttu-id="23ab5-126">這個屬性的有效值包括 `-1` 至 `2`、`147`、`483` 和 `647`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-126">Valid values for this property include `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="23ab5-127">如果此值為 `-1`，系統就不會從執行記錄資料表中刪除項目。</span><span class="sxs-lookup"><span data-stu-id="23ab5-127">If the value is `-1` entries are not deleted from the Execution Log table.</span></span> <span data-ttu-id="23ab5-128">預設值是 `60`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-128">The default value is `60`.</span></span>  
  
 <span data-ttu-id="23ab5-129">**SessionTimeout**</span><span class="sxs-lookup"><span data-stu-id="23ab5-129">**SessionTimeout**</span></span>  
 <span data-ttu-id="23ab5-130">工作階段維持作用中狀態的時間長度 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-130">The length of time, in seconds, that a session remains active.</span></span> <span data-ttu-id="23ab5-131">預設值是 `600`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-131">The default value is `600`.</span></span>  
  
 <span data-ttu-id="23ab5-132">**SharePointIntegratedMode**</span><span class="sxs-lookup"><span data-stu-id="23ab5-132">**SharePointIntegratedMode**</span></span>  
 <span data-ttu-id="23ab5-133">這是指出伺服器模式的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="23ab5-133">This is a read-only property that indicates the server mode.</span></span> <span data-ttu-id="23ab5-134">如果此值為 False，報表伺服器就會以原生模式執行。</span><span class="sxs-lookup"><span data-stu-id="23ab5-134">If this value is False, the report server runs in native mode.</span></span>  
  
 <span data-ttu-id="23ab5-135">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="23ab5-135">**SiteName**</span></span>  
 <span data-ttu-id="23ab5-136">顯示在報表管理員頁面標題中的報表伺服器網站名稱。</span><span class="sxs-lookup"><span data-stu-id="23ab5-136">The name of the report server site displayed in the page title of Report Manager.</span></span> <span data-ttu-id="23ab5-137">預設值是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23ab5-137">The default value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="23ab5-138">這個屬性可以是空字串。</span><span class="sxs-lookup"><span data-stu-id="23ab5-138">This property can be an empty string.</span></span> <span data-ttu-id="23ab5-139">最大長度是 8,000 個字元。</span><span class="sxs-lookup"><span data-stu-id="23ab5-139">The maximum length is 8,000 characters.</span></span>  
  
 <span data-ttu-id="23ab5-140">**StoredParametersLifetime**</span><span class="sxs-lookup"><span data-stu-id="23ab5-140">**StoredParametersLifetime**</span></span>  
 <span data-ttu-id="23ab5-141">指定預存參數可儲存的最大天數。</span><span class="sxs-lookup"><span data-stu-id="23ab5-141">Specifies the maximum number of days that a stored parameter can be stored.</span></span> <span data-ttu-id="23ab5-142">有效值為 `-1`、`+1` 至 `2,147,483,647`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-142">Valid values are `-1`, `+1` through `2,147,483,647`.</span></span> <span data-ttu-id="23ab5-143">預設值為 `180` 天。</span><span class="sxs-lookup"><span data-stu-id="23ab5-143">The default value is `180` days.</span></span>  
  
 <span data-ttu-id="23ab5-144">**StoredParametersThreshold**</span><span class="sxs-lookup"><span data-stu-id="23ab5-144">**StoredParametersThreshold**</span></span>  
 <span data-ttu-id="23ab5-145">指定報表伺服器可儲存的最大參數值數目。</span><span class="sxs-lookup"><span data-stu-id="23ab5-145">Specifies the maximum number of parameter values that can be stored by the report server.</span></span> <span data-ttu-id="23ab5-146">有效值為 `-1`、`+1` 至 `2,147,483,647`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-146">Valid values are `-1`, `+1` through `2,147,483,647`.</span></span> <span data-ttu-id="23ab5-147">預設值是 `1500`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-147">The default value is `1500`.</span></span>  
  
 <span data-ttu-id="23ab5-148">**UseSessionCookies**</span><span class="sxs-lookup"><span data-stu-id="23ab5-148">**UseSessionCookies**</span></span>  
 <span data-ttu-id="23ab5-149">指出報表伺服器與用戶端瀏覽器通訊時是否應該使用工作階段 Cookie。</span><span class="sxs-lookup"><span data-stu-id="23ab5-149">Indicates whether the report server should use session cookies when communicating with client browsers.</span></span> <span data-ttu-id="23ab5-150">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-150">The default value is `true`.</span></span>  
  
 <span data-ttu-id="23ab5-151">**ExternalImagesTimeout**</span><span class="sxs-lookup"><span data-stu-id="23ab5-151">**ExternalImagesTimeout**</span></span>  
 <span data-ttu-id="23ab5-152">決定在連接逾時之前，必須抓取外部影像檔案的時間長度。預設值為 `600` 秒。</span><span class="sxs-lookup"><span data-stu-id="23ab5-152">Determines the length of time within which an external image file must be retrieved before the connection is timed out. The default is `600` seconds.</span></span>  
  
 <span data-ttu-id="23ab5-153">**SnapshotCompression**</span><span class="sxs-lookup"><span data-stu-id="23ab5-153">**SnapshotCompression**</span></span>  
 <span data-ttu-id="23ab5-154">定義快照集的壓縮方式。</span><span class="sxs-lookup"><span data-stu-id="23ab5-154">Defines how snapshots are compressed.</span></span> <span data-ttu-id="23ab5-155">預設值是 `SQL`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-155">The default value is `SQL`.</span></span> <span data-ttu-id="23ab5-156">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="23ab5-156">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="23ab5-157">**SQL =** 當快照集儲存在報表伺服器資料庫時，系統會壓縮快照集。</span><span class="sxs-lookup"><span data-stu-id="23ab5-157">**SQL =** Snapshots are compressed when stored in the report server database.</span></span> <span data-ttu-id="23ab5-158">這是目前的行為。</span><span class="sxs-lookup"><span data-stu-id="23ab5-158">This is the current behavior.</span></span>  
  
 <span data-ttu-id="23ab5-159">**無 =** 系統不會壓縮快照集。</span><span class="sxs-lookup"><span data-stu-id="23ab5-159">**None** = Snapshots are not compressed.</span></span>  
  
 <span data-ttu-id="23ab5-160">**全部 =** 系統會針對所有儲存選項壓縮快照集，包括報表伺服器資料庫或是檔案系統。</span><span class="sxs-lookup"><span data-stu-id="23ab5-160">**All =** Snapshots are compressed for all storage options, which include the report server database or the file system.</span></span>  
  
 <span data-ttu-id="23ab5-161">**SystemReportTimeout**</span><span class="sxs-lookup"><span data-stu-id="23ab5-161">**SystemReportTimeout**</span></span>  
 <span data-ttu-id="23ab5-162">在報表伺服器命名空間中管理之所有報表的預設報表處理逾時值 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-162">The default report processing timeout value, in seconds, for all reports managed in the report server namespace.</span></span> <span data-ttu-id="23ab5-163">在報表層級可以覆寫這個值。</span><span class="sxs-lookup"><span data-stu-id="23ab5-163">This value can be overridden at the report level.</span></span> <span data-ttu-id="23ab5-164">如果已設定此屬性，當指定的時間已過期時，報表伺服器就會嘗試停止處理報表。</span><span class="sxs-lookup"><span data-stu-id="23ab5-164">If this property is set, the report server attempts to stop the processing of a report when the specified time has expired.</span></span> <span data-ttu-id="23ab5-165">有效值是從 `-1` 到 `2`、`147`、`483`、`647`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-165">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="23ab5-166">如果此值為 `-1`，命名空間中的報表就不會在處理期間逾時。</span><span class="sxs-lookup"><span data-stu-id="23ab5-166">If the value is `-1`, reports in the namespace do not time out during processing.</span></span> <span data-ttu-id="23ab5-167">預設值是 `1800`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-167">The default value is `1800`.</span></span>  
  
 <span data-ttu-id="23ab5-168">**SystemSnapshotLimit**</span><span class="sxs-lookup"><span data-stu-id="23ab5-168">**SystemSnapshotLimit**</span></span>  
 <span data-ttu-id="23ab5-169">針對報表所儲存之快照集的最大數目。</span><span class="sxs-lookup"><span data-stu-id="23ab5-169">The maximum number of snapshots that are stored for a report.</span></span> <span data-ttu-id="23ab5-170">有效值是從 `-1` 到 `2`、`147`、`483`、`647`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-170">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="23ab5-171">如果此值為 `-1`，表示沒有任何快照集限制。</span><span class="sxs-lookup"><span data-stu-id="23ab5-171">If the value is `-1`, there is no snapshot limit.</span></span>  
  
 <span data-ttu-id="23ab5-172">**EnableIntegratedSecurity**</span><span class="sxs-lookup"><span data-stu-id="23ab5-172">**EnableIntegratedSecurity**</span></span>  
 <span data-ttu-id="23ab5-173">決定 Windows 整合式安全性是否支援報表資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="23ab5-173">Determines whether Windows integrated security is supported for report data source connections.</span></span> <span data-ttu-id="23ab5-174">預設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-174">The default is `True`.</span></span> <span data-ttu-id="23ab5-175">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="23ab5-175">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="23ab5-176">`True` = Windows 整合式安全性已啟用。</span><span class="sxs-lookup"><span data-stu-id="23ab5-176">`True` = Windows integrated security is enabled.</span></span>  
  
 <span data-ttu-id="23ab5-177">`False` = Windows 整合式安全性未啟用。</span><span class="sxs-lookup"><span data-stu-id="23ab5-177">`False` = Windows integrated security is not enabled.</span></span> <span data-ttu-id="23ab5-178">設定為使用 Windows 整合式安全性的報表資料來源不會執行。</span><span class="sxs-lookup"><span data-stu-id="23ab5-178">Report data sources that are configured to use Windows integrated security will not run.</span></span>  
  
 `EnableLoadReportDefinition`  
 <span data-ttu-id="23ab5-179">選取此選項即可指定使用者是否可以從報表產生器報表執行特定報表執行。</span><span class="sxs-lookup"><span data-stu-id="23ab5-179">Select this option to specify whether users can perform ad hoc report execution from a Report Builder report.</span></span> <span data-ttu-id="23ab5-180">設定這個選項會針對報表伺服器決定 `EnableLoadReportDefinition` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="23ab5-180">Setting this option determines the value of the `EnableLoadReportDefinition` property on the report server.</span></span>  
  
 <span data-ttu-id="23ab5-181">如果您清除此選項，這個屬性將會設定為 False 而且報表伺服器將不會針對使用報表模型做為資料來源的報表產生點選連結報表。</span><span class="sxs-lookup"><span data-stu-id="23ab5-181">If you clear this option, the property will be set to False and report server will not generate clickthrough reports for reports that use a report model as a data source.</span></span> <span data-ttu-id="23ab5-182">LoadReportDefinition 方法的任何呼叫都會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="23ab5-182">Any calls to the LoadReportDefinition method will be blocked.</span></span>  
  
 <span data-ttu-id="23ab5-183">關閉此選項可減少惡意使用者利用 LoadReportDefinition 要求讓報表伺服器超過負載，藉以啟動阻斷服務攻擊的威脅。</span><span class="sxs-lookup"><span data-stu-id="23ab5-183">Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with LoadReportDefinition requests.</span></span>  
  
 <span data-ttu-id="23ab5-184">**EnableRemoteErrors**</span><span class="sxs-lookup"><span data-stu-id="23ab5-184">**EnableRemoteErrors**</span></span>  
 <span data-ttu-id="23ab5-185">包含外部錯誤資訊 (例如，有關報表資料來源的錯誤資訊) 以及針對從遠端電腦要求報表之使用者傳回的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="23ab5-185">Includes external error information (for example, error information about report data sources) with the error messages that are returned for users who request reports from remote computers.</span></span> <span data-ttu-id="23ab5-186">有效值為 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-186">Valid values are `true` and `false`.</span></span> <span data-ttu-id="23ab5-187">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-187">The default value is `false`.</span></span> <span data-ttu-id="23ab5-188">如需詳細資訊，請參閱[啟用遠端錯誤 &#40;Reporting Services&#41;](../report-server/enable-remote-errors-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-188">For more information, see [Enable Remote Errors &#40;Reporting Services&#41;](../report-server/enable-remote-errors-reporting-services.md).</span></span>  
  
 <span data-ttu-id="23ab5-189">**EnableReportDesignClientDownload**</span><span class="sxs-lookup"><span data-stu-id="23ab5-189">**EnableReportDesignClientDownload**</span></span>  
 <span data-ttu-id="23ab5-190">指定是否可從報表伺服器下載報表產生器安裝套件。</span><span class="sxs-lookup"><span data-stu-id="23ab5-190">Specifies whether Report Builder installation package can be downloaded from the report server.</span></span> <span data-ttu-id="23ab5-191">如果您清除此設定，報表產生器的 URL 將會失效。</span><span class="sxs-lookup"><span data-stu-id="23ab5-191">If you clear this setting, the URL to Report Builder will not work.</span></span> <span data-ttu-id="23ab5-192">如需詳細資訊，請參閱 [設定報表產生器的存取](../report-server/configure-report-builder-access.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-192">For more information, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
 <span data-ttu-id="23ab5-193">**EditSessionCacheLimit**</span><span class="sxs-lookup"><span data-stu-id="23ab5-193">**EditSessionCacheLimit**</span></span>  
 <span data-ttu-id="23ab5-194">指定可以在報表編輯工作階段中使用的資料快取項目數目。</span><span class="sxs-lookup"><span data-stu-id="23ab5-194">Specifies the number of data cache entries that can be active in a report edit session.</span></span> <span data-ttu-id="23ab5-195">預設數目是 5。</span><span class="sxs-lookup"><span data-stu-id="23ab5-195">The default number is 5.</span></span>  
  
 <span data-ttu-id="23ab5-196">**EditSessionTimeout**</span><span class="sxs-lookup"><span data-stu-id="23ab5-196">**EditSessionTimeout**</span></span>  
 <span data-ttu-id="23ab5-197">指定報表編輯會話超時之前的秒數。預設值為7200秒 (2 小時) 。</span><span class="sxs-lookup"><span data-stu-id="23ab5-197">Specifies the number of seconds until a report edit session times out. The default value is 7200 seconds (2 hours).</span></span>  
  
 <span data-ttu-id="23ab5-198">**EnableTestConnectionDetailedErrors**</span><span class="sxs-lookup"><span data-stu-id="23ab5-198">**EnableTestConnectionDetailedErrors**</span></span>  
 <span data-ttu-id="23ab5-199">指出當使用者使用報表伺服器來測試資料來源連接時，是否要將詳細的錯誤訊息傳送至用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="23ab5-199">Indicates whether detailed error messages are sent to the client computer when users test data source connections using the report server.</span></span> <span data-ttu-id="23ab5-200">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="23ab5-200">The default value is `true`.</span></span> <span data-ttu-id="23ab5-201">如果此選項設定為 `false`，就只會傳送一般錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="23ab5-201">If the option is set to `false`, only generic error messages are sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ab5-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ab5-202">See Also</span></span>  
 <span data-ttu-id="23ab5-203">[將報表伺服器屬性設定 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-203">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="23ab5-204">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-204">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="23ab5-205">[Reporting Services 屬性](../report-server-web-service/net-framework/reporting-services-properties.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-205">[Reporting Services Properties](../report-server-web-service/net-framework/reporting-services-properties.md) </span></span>  
 <span data-ttu-id="23ab5-206">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-206">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="23ab5-207">[報表伺服器系統屬性](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-207">[Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) </span></span>  
 <span data-ttu-id="23ab5-208">[編寫部署和管理工作的腳本](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-208">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 [<span data-ttu-id="23ab5-209">啟用與停用我的報表</span><span class="sxs-lookup"><span data-stu-id="23ab5-209">Enable and Disable My Reports</span></span>](../report-server/enable-and-disable-my-reports.md)  
  
  
