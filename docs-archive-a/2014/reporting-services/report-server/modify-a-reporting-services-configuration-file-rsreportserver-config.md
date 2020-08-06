---
title: 修改 Reporting Services 設定檔 (RSreportserver.config) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 958ef51f-2699-4cb2-a92e-3b4322e36a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75ff276a0ba43cb89393466bf40a71b7acd21368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595644"
---
# <a name="modify-a-reporting-services-configuration-file-rsreportserverconfig"></a><span data-ttu-id="3d00e-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span><span class="sxs-lookup"><span data-stu-id="3d00e-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="3d00e-103">會將應用程式設定儲存在組態檔集合中。</span><span class="sxs-lookup"><span data-stu-id="3d00e-103">stores application settings in a set of configuration files.</span></span> <span data-ttu-id="3d00e-104">安裝程式會針對您所安裝的每個報表伺服器執行個體建立組態檔。</span><span class="sxs-lookup"><span data-stu-id="3d00e-104">Setup creates the configuration files for each report server instance you install.</span></span> <span data-ttu-id="3d00e-105">在每個檔案內部，其值是在安裝期間設定，或當您使用工具和應用程式來設定作業的伺服器時設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-105">Within each file, values are either set during installation or when you use tools and applications to configure a server for operation.</span></span> <span data-ttu-id="3d00e-106">在某些情況下，您必須直接修改檔案，以便加入或修改進階設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-106">In some cases, you must modify a file directly to add or configure advanced settings.</span></span> <span data-ttu-id="3d00e-107">組態設定會指定為 XML 元素或屬性。</span><span class="sxs-lookup"><span data-stu-id="3d00e-107">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="3d00e-108">如果您了解 XML 和組態檔，就可以使用文字或程式碼編輯器來修改可由使用者定義的設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-108">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span>  
  
 <span data-ttu-id="3d00e-109">某些組態設定只能透過某個工具進行設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-109">Some configuration settings can be set only through a tool.</span></span> <span data-ttu-id="3d00e-110">您必須透過 Reporting Services 組態工具、安裝程式或 **rsconfig** 命令列公用程式來修改包含加密值的設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-110">Settings that contain encrypted values must be modified through the Reporting Services Configuration tool, the Setup program, or the **rsconfig** command line utility.</span></span> <span data-ttu-id="3d00e-111">您必須是本機管理員群組的成員才能執行這些工具。</span><span class="sxs-lookup"><span data-stu-id="3d00e-111">You must be a member of the local Administrators group to run these tools.'</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d00e-112">修改組態檔時，請特別小心。</span><span class="sxs-lookup"><span data-stu-id="3d00e-112">Use caution when modifying configuration files.</span></span> <span data-ttu-id="3d00e-113">如果您修改保留給內部使用的設定，可能會停用安裝程序。</span><span class="sxs-lookup"><span data-stu-id="3d00e-113">If you modify a setting that is reserved for internal use, you may disable your installation.</span></span> <span data-ttu-id="3d00e-114">除非您嘗試解決特定問題，否則一般而言不建議您修改組態設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-114">Generally, modifying configuration settings is not recommended unless you are trying to solve a specific problem.</span></span> <span data-ttu-id="3d00e-115">如需有關哪些設定可安全變更的詳細資訊，請參閱＜ [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) ＞或＜ [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3d00e-115">For more information about which settings are safe to change, see [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) or [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).</span></span> <span data-ttu-id="3d00e-116">如需組態檔的詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 產品文件。</span><span class="sxs-lookup"><span data-stu-id="3d00e-116">For more information about configuration files, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span>  
  
 <span data-ttu-id="3d00e-117">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="3d00e-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="3d00e-118">讀取和使用組態值</span><span class="sxs-lookup"><span data-stu-id="3d00e-118">Reading and Using Configuration Values</span></span>](#bkmk_read_values)  
  
-   [<span data-ttu-id="3d00e-119">關於預設值</span><span class="sxs-lookup"><span data-stu-id="3d00e-119">About Default Values</span></span>](#bkmk_default_values)  
  
-   [<span data-ttu-id="3d00e-120">刪除組態設定</span><span class="sxs-lookup"><span data-stu-id="3d00e-120">Deleting Configuration Settings</span></span>](#bkmk_delete_config_settings)  
  
-   [<span data-ttu-id="3d00e-121">編輯 Reporting Services 組態檔</span><span class="sxs-lookup"><span data-stu-id="3d00e-121">To Edit a Reporting Services Configuration File</span></span>](#bkmk_edit_configuation_file)  
  
##  <a name="reading-and-using-configuration-values"></a><a name="bkmk_read_values"></a> <span data-ttu-id="3d00e-122">讀取和使用組態值</span><span class="sxs-lookup"><span data-stu-id="3d00e-122">Reading and Using Configuration Values</span></span>  
 <span data-ttu-id="3d00e-123">當服務啟動時，以及每次系統儲存組態檔時，報表伺服器都會讀取組態檔。</span><span class="sxs-lookup"><span data-stu-id="3d00e-123">A report server reads the configuration files when the service starts and whenever the configuration file is saved.</span></span> <span data-ttu-id="3d00e-124">目前的應用程式網域過期之後，全新和修訂的值才會在新的應用程式網域中生效。</span><span class="sxs-lookup"><span data-stu-id="3d00e-124">New and revised values take effect in a new application domain after the current application domain expires.</span></span> <span data-ttu-id="3d00e-125">系統會盡可能讓仍然在目前應用程式網域中處理的要求完成。</span><span class="sxs-lookup"><span data-stu-id="3d00e-125">Whenever possible, requests that are still processing in the current application domain are allowed to complete.</span></span> <span data-ttu-id="3d00e-126">不過，少數設定需要進行立即應用程式網域回收作業。</span><span class="sxs-lookup"><span data-stu-id="3d00e-126">However, a few settings require an immediate application domain recycle operation.</span></span> <span data-ttu-id="3d00e-127">在這種情況下，所有處理中的要求都會在新的應用程式網域中重新啟動。</span><span class="sxs-lookup"><span data-stu-id="3d00e-127">In this case, all requests that are in process are restarted in a new application domain.</span></span>  
  
 <span data-ttu-id="3d00e-128">如果報表伺服器偵測到無效的值，報表伺服器就會在 Windows 應用程式記錄中記錄錯誤，而且無法啟動或使用預設值 (視錯誤情況而定)：</span><span class="sxs-lookup"><span data-stu-id="3d00e-128">If the report server detects an invalid value, the report server logs an error to the Windows application log and either fails to start or uses a default value, depending on the error:</span></span>  
  
-   <span data-ttu-id="3d00e-129">如果錯誤是不正確的 XML，則報表伺服器將不會啟動。</span><span class="sxs-lookup"><span data-stu-id="3d00e-129">If the error is malformed XML, the report server will not start.</span></span> <span data-ttu-id="3d00e-130">如果您造成錯誤時，報表伺服器正在執行，報表伺服器就會忽略無效的組態檔，直到報表伺服器重新啟動或應用程式網域回收為止。</span><span class="sxs-lookup"><span data-stu-id="3d00e-130">If the report server is running when you introduce the error, the report server ignores the invalid configuration file until the report server restarts or the application domain is recycled.</span></span> <span data-ttu-id="3d00e-131">偵測到錯誤之後，報表伺服器將不會再啟動。</span><span class="sxs-lookup"><span data-stu-id="3d00e-131">Once the error is detected, the report server will no longer start.</span></span>  
  
-   <span data-ttu-id="3d00e-132">如果錯誤是無效的組態值，伺服器將使用內部預設值並在追蹤記錄檔中記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d00e-132">If the error is an invalid configuration value, the server will use internal default values and log an error to the trace log files.</span></span> <span data-ttu-id="3d00e-133">在內部預設值無法使用的少數情況下，如果無效的組態設定對於伺服器作業很重要，伺服器將傳回 rsServerConfigurationError 錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d00e-133">In the few cases where internal default values are not available, the server will return the rsServerConfigurationError error if the invalid configuration setting is critical to server operations.</span></span> <span data-ttu-id="3d00e-134">有關遺漏或無效重要設定的錯誤會以 HTML 錯誤頁面傳回用戶端應用程式並記錄在事件記錄中。</span><span class="sxs-lookup"><span data-stu-id="3d00e-134">Errors about missing or invalid critical settings are returned to the client application in an HTML error page and logged to the event log.</span></span>  
  
 <span data-ttu-id="3d00e-135">所有組態檔變更 (包括成功變更) 都會記錄在報表伺服器追蹤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="3d00e-135">All configuration file changes, including successful changes, are recorded in the report server trace log file.</span></span> <span data-ttu-id="3d00e-136">只有錯誤會記錄在應用程式事件記錄中。</span><span class="sxs-lookup"><span data-stu-id="3d00e-136">Only errors are logged to the application event log.</span></span>  
  
##  <a name="about-default-values"></a><a name="bkmk_default_values"></a> <span data-ttu-id="3d00e-137">關於預設值</span><span class="sxs-lookup"><span data-stu-id="3d00e-137">About Default Values</span></span>  
 <span data-ttu-id="3d00e-138">大部分組態設定都具有報表伺服器內部指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d00e-138">Most configuration settings have default values that are specified internally in the report server.</span></span> <span data-ttu-id="3d00e-139">如果使用者定義的值無效或未指定，報表伺服器就會使用這些值。</span><span class="sxs-lookup"><span data-stu-id="3d00e-139">The report server will use these values if a user-defined value is invalid or not specified.</span></span> <span data-ttu-id="3d00e-140">如果由於組態設定無效而必須使用預設值，系統就會在追蹤記錄檔中寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d00e-140">If a default value must be used due to an invalid configuration setting, an error is written to the trace log file.</span></span>  
  
##  <a name="deleting-configuration-settings"></a><a name="bkmk_delete_config_settings"></a> <span data-ttu-id="3d00e-141">刪除組態設定</span><span class="sxs-lookup"><span data-stu-id="3d00e-141">Deleting Configuration Settings</span></span>  
 <span data-ttu-id="3d00e-142">如果是有預設值的組態設定，從組態檔中移除此設定不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="3d00e-142">For configuration settings that have default values, removing the setting from the configuration file has no effect.</span></span> <span data-ttu-id="3d00e-143">大部分組態設定實際上都會在內部定義及設定。</span><span class="sxs-lookup"><span data-stu-id="3d00e-143">Most configuration settings are actually defined and configured internally.</span></span> <span data-ttu-id="3d00e-144">如果您刪除組態檔中的項目，內部複本仍然可以使用，而且會使用為它定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d00e-144">If you delete an item from the configuration file, the internal copy is still available and uses the default value that is defined for it.</span></span>  
  
##  <a name="to-edit-a-reporting-services-configuration-file"></a><a name="bkmk_edit_configuation_file"></a> <span data-ttu-id="3d00e-145">編輯 Reporting Services 組態檔</span><span class="sxs-lookup"><span data-stu-id="3d00e-145">To Edit a Reporting Services Configuration File</span></span>  
  
1.  <span data-ttu-id="3d00e-146">尋找您想要編輯的組態檔：</span><span class="sxs-lookup"><span data-stu-id="3d00e-146">Find the configuration file you want to edit:</span></span>  
  
    -   <span data-ttu-id="3d00e-147">**RSReportServer.config** 位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3d00e-147">**RSReportServer.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
        ```  
  
    -   <span data-ttu-id="3d00e-148">**RSReportServerServices.exe.config** 位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3d00e-148">**RSReportServerServices.exe.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\bin  
        ```  
  
    -   <span data-ttu-id="3d00e-149">**RSReportDesigner.config** 位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3d00e-149">**RSReportDesigner.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
        ```  
  
2.  <span data-ttu-id="3d00e-150">儲存檔案的副本，以防您需要回復變更。</span><span class="sxs-lookup"><span data-stu-id="3d00e-150">Save a copy of the file in case you need to roll back your changes.</span></span>  
  
3.  <span data-ttu-id="3d00e-151">在 [記事本] 或程式碼編輯器中開啟原始檔。</span><span class="sxs-lookup"><span data-stu-id="3d00e-151">Open the original file in Notepad or a code editor.</span></span> <span data-ttu-id="3d00e-152">請勿使用 Textpad，因為它會在儲存檔案之前設定檔案長度，進而導致系統在追蹤記錄檔中寫入無效字元錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d00e-152">Do not use Textpad; it sets the file length before the file is saved, causing an invalid character error to be written to the trace log file.</span></span>  
  
4.  <span data-ttu-id="3d00e-153">輸入您想要加入或使用的元素或值。</span><span class="sxs-lookup"><span data-stu-id="3d00e-153">Type the element or value that you want to add or use.</span></span> <span data-ttu-id="3d00e-154">元素會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3d00e-154">Elements are case-sensitive.</span></span> <span data-ttu-id="3d00e-155">如果您要加入元素，請務必使用正確的大小寫字母。</span><span class="sxs-lookup"><span data-stu-id="3d00e-155">If you are adding an element, be sure to use the correct upper and lower case letters.</span></span> <span data-ttu-id="3d00e-156">如果您要自訂轉譯延伸模組、驗證延伸模組或資料處理延伸模組，請使用編輯組態檔的特定指示。</span><span class="sxs-lookup"><span data-stu-id="3d00e-156">Specific instructions for editing configuration files are available if you are customizing rendering extension, authentication extensions, or data processing extensions:</span></span>  
  
    -   [<span data-ttu-id="3d00e-157">報表伺服器的驗證</span><span class="sxs-lookup"><span data-stu-id="3d00e-157">Authentication with the Report Server</span></span>](../security/authentication-with-the-report-server.md)  
  
    -   [<span data-ttu-id="3d00e-158">設定報表管理員傳遞自訂驗證 Cookie</span><span class="sxs-lookup"><span data-stu-id="3d00e-158">Configure Report Manager to Pass Custom Authentication Cookies</span></span>](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)  
  
    -   [<span data-ttu-id="3d00e-159">在 RSReportServer.Config 中自訂轉譯延伸模組參數</span><span class="sxs-lookup"><span data-stu-id="3d00e-159">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](../customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
5.  <span data-ttu-id="3d00e-160">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3d00e-160">Save the file.</span></span>  
  
6.  <span data-ttu-id="3d00e-161">檢查追蹤記錄檔，以便確認錯誤並未發生。</span><span class="sxs-lookup"><span data-stu-id="3d00e-161">Check the trace log files to verify that errors did not occur.</span></span> <span data-ttu-id="3d00e-162">如果您看見錯誤狀況，表示某項設定或其值的指定內容不正確。</span><span class="sxs-lookup"><span data-stu-id="3d00e-162">If you see error conditions, a setting or its value is specified incorrectly.</span></span> <span data-ttu-id="3d00e-163">請檢閱＜ [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) ＞，以便取得導致錯誤發生之任何設定的有效值。</span><span class="sxs-lookup"><span data-stu-id="3d00e-163">Review the [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) for valid values for any setting that is causing an error.</span></span> <span data-ttu-id="3d00e-164">如需如何檢視追蹤記錄的詳細資訊，請參閱 [報表伺服器服務追蹤記錄](report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="3d00e-164">For more information about how to view the trace log, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d00e-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d00e-165">See Also</span></span>  
 <span data-ttu-id="3d00e-166">[Rsreportserver.config 設定檔](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-166">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="3d00e-167">[ReportingServicesService 設定檔](reportingservicesservice-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-167">[ReportingServicesService Configuration File](reportingservicesservice-configuration-file.md) </span></span>  
 <span data-ttu-id="3d00e-168">[Rsreportdesigner.config 設定檔](rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-168">[RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="3d00e-169">[部署資料處理延伸模組](../extensions/data-processing/deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-169">[Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="3d00e-170">[部署傳遞延伸模組](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-170">[Deploying a Delivery Extension](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="3d00e-171">[部署轉譯延伸模組](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-171">[Deploying a Rendering Extension](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="3d00e-172">[如何：部署自訂報表專案](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="3d00e-172">[How to: Deploy a Custom Report Item](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="3d00e-173">Reporting Services 組態檔</span><span class="sxs-lookup"><span data-stu-id="3d00e-173">Reporting Services Configuration Files</span></span>](reporting-services-configuration-files.md)  
  
  
