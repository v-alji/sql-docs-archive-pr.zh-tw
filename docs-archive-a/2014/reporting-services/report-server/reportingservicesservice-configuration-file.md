---
title: ReportingServicesService 設定檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5124631db9635211827dd3b1abbff7116101a61d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596489"
---
# <a name="reportingservicesservice-configuration-file"></a><span data-ttu-id="7fb5f-102">ReportingServicesService 組態檔</span><span class="sxs-lookup"><span data-stu-id="7fb5f-102">ReportingServicesService Configuration File</span></span>
  <span data-ttu-id="7fb5f-103">ReportingServicesService.exe.config 檔包括設定追蹤的設定。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-103">The ReportingServicesService.exe.config file includes settings that configure tracing.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="7fb5f-104">檔案位置</span><span class="sxs-lookup"><span data-stu-id="7fb5f-104">File Location</span></span>  
 <span data-ttu-id="7fb5f-105">此檔案位於 \Reporting Services\Report Server\Bin 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-105">This file is located in the \Reporting Services\Report Server\Bin folder.</span></span>  
  
## <a name="editing-guidelines"></a><span data-ttu-id="7fb5f-106">編輯指導方針</span><span class="sxs-lookup"><span data-stu-id="7fb5f-106">Editing Guidelines</span></span>  
 <span data-ttu-id="7fb5f-107">您可以修改此檔案以重新命名記錄檔，或者增加或減少追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-107">You can modify this file to rename the log file or to increase or decrease trace levels.</span></span> <span data-ttu-id="7fb5f-108">請勿修改其他任何設定。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-108">Do not modify any of the other settings.</span></span> <span data-ttu-id="7fb5f-109">如需指示，請參閱[修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-109">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="7fb5f-110">如需追蹤紀錄的詳細資訊，請參閱 [報表伺服器服務追蹤記錄](report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-110">For more information about trace logs, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="7fb5f-111">設定範例</span><span class="sxs-lookup"><span data-stu-id="7fb5f-111">Example Configuration</span></span>  
 <span data-ttu-id="7fb5f-112">下列範例顯示 ReportingServicesService.exe.config 檔中的設定和預設值。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-112">The following example shows the settings and default values found in the ReportingServicesService.exe.config file.</span></span>  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="7fb5f-113">組態設定</span><span class="sxs-lookup"><span data-stu-id="7fb5f-113">Configuration Settings</span></span>  
 <span data-ttu-id="7fb5f-114">下表提供有關特定設定的資訊。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-114">The following table provides information about specific settings.</span></span> <span data-ttu-id="7fb5f-115">設定會依其出現在組態檔的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-115">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="7fb5f-116">設定</span><span class="sxs-lookup"><span data-stu-id="7fb5f-116">Setting</span></span>|<span data-ttu-id="7fb5f-117">描述</span><span class="sxs-lookup"><span data-stu-id="7fb5f-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fb5f-118">**RStrace**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-118">**RStrace**</span></span>|<span data-ttu-id="7fb5f-119">指定用於錯誤和追蹤的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-119">Specifies namespaces used for errors and tracing.</span></span>|  
|<span data-ttu-id="7fb5f-120">**DefaultTraceSwitch**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-120">**DefaultTraceSwitch**</span></span>|<span data-ttu-id="7fb5f-121">指定報告到 ReportServerService 追蹤記錄的資訊層級。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-121">Specifies the level of information that is reported to the ReportServerService trace log.</span></span> <span data-ttu-id="7fb5f-122">每一個層級包括所有較低層級所報告的資訊。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-122">Each level includes the information reported by all lower-numbered levels.</span></span> <span data-ttu-id="7fb5f-123">不建議停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-123">Disabling tracing is not recommended.</span></span> <span data-ttu-id="7fb5f-124">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="7fb5f-124">Valid values include:</span></span><br /><br /> <span data-ttu-id="7fb5f-125">0= 停用追蹤</span><span class="sxs-lookup"><span data-stu-id="7fb5f-125">0= Disables tracing</span></span><br /><br /> <span data-ttu-id="7fb5f-126">1= 例外狀況和重新啟動</span><span class="sxs-lookup"><span data-stu-id="7fb5f-126">1= Exceptions and restarts</span></span><br /><br /> <span data-ttu-id="7fb5f-127">2= 例外、重新啟動和警告</span><span class="sxs-lookup"><span data-stu-id="7fb5f-127">2= Exceptions, restarts, warnings</span></span><br /><br /> <span data-ttu-id="7fb5f-128">3= 例外、重新啟動、警告和狀態訊息 (預設值)</span><span class="sxs-lookup"><span data-stu-id="7fb5f-128">3= Exceptions, restarts, warnings, status messages (default)</span></span><br /><br /> <span data-ttu-id="7fb5f-129">4= 詳細資訊模式</span><span class="sxs-lookup"><span data-stu-id="7fb5f-129">4= Verbose mode</span></span>|  
|<span data-ttu-id="7fb5f-130">**FileName**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-130">**FileName**</span></span>|<span data-ttu-id="7fb5f-131">指定記錄檔名稱的第一部分。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-131">Specifies the first portion of the log file name.</span></span> <span data-ttu-id="7fb5f-132">`Prefix` 所指定的值會完成名稱的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-132">The value specified by `Prefix` completes the rest of the name.</span></span> <span data-ttu-id="7fb5f-133">依預設，名稱是 ReportServerService_。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-133">By default, the name is ReportServerService_.</span></span>|  
|<span data-ttu-id="7fb5f-134">**FileSizeLimitMb**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-134">**FileSizeLimitMb**</span></span>|<span data-ttu-id="7fb5f-135">指定追蹤記錄的大小上限。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-135">Specifies an upper limit on trace log size.</span></span> <span data-ttu-id="7fb5f-136">檔案大小的單位為 MB。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-136">The file is measured in megabytes.</span></span> <span data-ttu-id="7fb5f-137">有效值為 0 到最大整數。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-137">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="7fb5f-138">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-138">The default value is 32.</span></span>|  
|<span data-ttu-id="7fb5f-139">**KeepFilesForDays**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-139">**KeepFilesForDays**</span></span>|<span data-ttu-id="7fb5f-140">指定一個天數，超過此天數後，追蹤記錄檔便會被刪除。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-140">Specifies the number of days after which a trace log file will be deleted.</span></span> <span data-ttu-id="7fb5f-141">有效值為 0 到最大整數。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-141">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="7fb5f-142">預設值為 14。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-142">The default value is 14.</span></span>|  
|`Prefix`|<span data-ttu-id="7fb5f-143">指定可區別記錄檔執行個體的產生值。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-143">Specifies a generated value that distinguishes one log instance from another.</span></span> <span data-ttu-id="7fb5f-144">依預設，會將時間戳記附加至追蹤記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-144">By default, timestamp values are appended to trace log file names.</span></span> <span data-ttu-id="7fb5f-145">此值設定為 "tid, time"。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-145">This value is set to " tid, time ".</span></span> <span data-ttu-id="7fb5f-146">請勿修改此設定。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-146">Do not modify this setting.</span></span>|  
|<span data-ttu-id="7fb5f-147">**TraceListeners**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-147">**TraceListeners**</span></span>|<span data-ttu-id="7fb5f-148">指定輸出追蹤記錄內容的目標。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-148">Specifies a target for outputting trace log content.</span></span> <span data-ttu-id="7fb5f-149">您可以指定多重目標，每個目標之間請以逗號隔開。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-149">You can specify multiple targets using a comma to separate each one.</span></span> <span data-ttu-id="7fb5f-150">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="7fb5f-150">Valid values include:</span></span><br /><br /> <span data-ttu-id="7fb5f-151">DebugWindow (預設值)</span><span class="sxs-lookup"><span data-stu-id="7fb5f-151">DebugWindow (default)</span></span><br /><br /> <span data-ttu-id="7fb5f-152">File (預設值)</span><span class="sxs-lookup"><span data-stu-id="7fb5f-152">File (default)</span></span><br /><br /> <span data-ttu-id="7fb5f-153">StdOut</span><span class="sxs-lookup"><span data-stu-id="7fb5f-153">StdOut</span></span>|  
|<span data-ttu-id="7fb5f-154">**TraceFileMode**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-154">**TraceFileMode**</span></span>|<span data-ttu-id="7fb5f-155">指定追蹤記錄中是否要包含 24 小時內的資料。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-155">Specifies whether trace logs contain data for a 24-hour period.</span></span> <span data-ttu-id="7fb5f-156">每個元件每一天只能有一份追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-156">You should have one unique trace log for each component on each day.</span></span> <span data-ttu-id="7fb5f-157">此值設定為「Unique (預設值)」。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-157">This value is set to "Unique (default)".</span></span> <span data-ttu-id="7fb5f-158">請勿修改此值。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-158">Do not modify this value.</span></span>|  
|<span data-ttu-id="7fb5f-159">**元件**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-159">**Components**</span></span>|<span data-ttu-id="7fb5f-160">指定建立追蹤記錄的元件。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-160">Specifies the components for which trace logs are created.</span></span> <span data-ttu-id="7fb5f-161">預設值是 `all`。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-161">The default value is `all`.</span></span> <span data-ttu-id="7fb5f-162">此設定的其他有效值包括內部元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-162">Other valid values for this setting include the names of internal components.</span></span> <span data-ttu-id="7fb5f-163">請勿修改此值。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-163">Do not modify this value.</span></span>|  
|<span data-ttu-id="7fb5f-164">**運行**</span><span class="sxs-lookup"><span data-stu-id="7fb5f-164">**Runtime**</span></span>|<span data-ttu-id="7fb5f-165">指定支援與前版回溯相容的組態設定。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-165">Specifies configuration settings that support backward compatibility with the previous version.</span></span> <span data-ttu-id="7fb5f-166">執行階段設定是用來重新導向以新版為前版 Microsoft.ReportingServices.Interfaces 之目標的要求。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-166">Runtime settings are used to redirect requests that target the previous version of Microsoft.ReportingServices.Interfaces to the new version.</span></span><br /><br /> <span data-ttu-id="7fb5f-167">本節中的所有組態設定會在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 產品文件集中加以描述。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-167">All of the configuration settings in this section are described in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span> <span data-ttu-id="7fb5f-168">如需詳細資訊，請在 MSDN 網站上或 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 文件集中搜尋「執行階段結構描述設定」。</span><span class="sxs-lookup"><span data-stu-id="7fb5f-168">For more information, search for "Runtime Schema Settings" on the MSDN Web site or in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fb5f-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb5f-169">See Also</span></span>  
 <span data-ttu-id="7fb5f-170">[Reporting Services 組態檔](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="7fb5f-170">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="7fb5f-171">報表伺服器服務追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="7fb5f-171">Report Server Service Trace Log</span></span>](report-server-service-trace-log.md)  
  
  
