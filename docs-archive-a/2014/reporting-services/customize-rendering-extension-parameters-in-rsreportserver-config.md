---
title: 在 RSReportServer.Config 中自訂轉譯延伸模組參數 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35a01e12fa4016d03717b008e4241c3be5e55236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708997"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a><span data-ttu-id="8663f-102">在 RSReportServer.Config 中自訂轉譯延伸模組參數</span><span class="sxs-lookup"><span data-stu-id="8663f-102">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>
  <span data-ttu-id="8663f-103">您可以在 RSReportServer 組態檔中指定轉譯延伸模組參數，以便覆寫在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器上執行之報表的預設報表轉譯行為。</span><span class="sxs-lookup"><span data-stu-id="8663f-103">You can specify rendering extension parameters in the RSReportServer configuration file to override default report rendering behavior for reports that run on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="8663f-104">您可以修改轉譯延伸模組參數來達成下列目標：</span><span class="sxs-lookup"><span data-stu-id="8663f-104">You can modify rendering extension parameters to achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="8663f-105">變更轉譯延伸模組名稱在報表工具列 [匯出] 清單中的顯示方式 (例如，將「網頁封存」變更為「MHTML」)，或者將該名稱翻譯為不同的語言。</span><span class="sxs-lookup"><span data-stu-id="8663f-105">Change how the rendering extension name appears in the Export list of the report toolbar (for example, to change "Web archive" to "MHTML"), or localize the name to a different language.</span></span>  
  
-   <span data-ttu-id="8663f-106">建立同一個轉譯延伸模組的多個執行個體，以支援不同的報表呈現選項 (例如，影像轉譯延伸模組的縱向及橫向模式版本)。</span><span class="sxs-lookup"><span data-stu-id="8663f-106">Create multiple instances of the same rendering extension to support different report presentation options (for example, a portrait and landscape mode version of the Image rendering extension).</span></span>  
  
-   <span data-ttu-id="8663f-107">變更預設轉譯延伸模組參數，以使用不同的值 (例如，影像轉譯延伸模組使用 TIFF 做為預設的輸出格式；您可以修改該參數，改為使用 EMF)。</span><span class="sxs-lookup"><span data-stu-id="8663f-107">Change the default rendering extension parameters to use different values (for example, the Image rendering extension uses TIFF as the default output format; you can modify the extension parameters to use EMF instead).</span></span>  
  
 <span data-ttu-id="8663f-108">變更轉譯延伸模組參數只會影響報表伺服器上的轉譯作業。</span><span class="sxs-lookup"><span data-stu-id="8663f-108">Changing the rendering extension parameters only affects rendering operations on the report server.</span></span> <span data-ttu-id="8663f-109">您無法覆寫報表設計師中報表預覽的轉譯延伸模組設定。</span><span class="sxs-lookup"><span data-stu-id="8663f-109">You cannot override rendering extension settings in report preview in Report Designer.</span></span>  
  
 <span data-ttu-id="8663f-110">指定組態檔中的轉譯延伸模組參數，會對轉譯延伸模組造成全域的影響。</span><span class="sxs-lookup"><span data-stu-id="8663f-110">Specifying rendering extension parameters in the configuration files affects rendering extensions globally.</span></span> <span data-ttu-id="8663f-111">只要使用特定的轉譯延伸模組，組態檔中的設定就會取代預設值。</span><span class="sxs-lookup"><span data-stu-id="8663f-111">The settings in the configuration files are used in place of default values whenever a particular rendering extension is used.</span></span> <span data-ttu-id="8663f-112">如果您要針對特定報表或轉譯作業設定轉譯延伸模組參數，就必須使用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法以程式設計的方式指定裝置資訊，或在報表 URL 上指定裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8663f-112">If you want to set rendering extension parameters for a specific report or render operation, you must specify device information programmatically using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method or by specifying device information settings on a report URL.</span></span> <span data-ttu-id="8663f-113">如需針對轉譯作業指定裝置資訊設定，以及檢視裝置資訊設定之完整清單的詳細資訊，請參閱 [將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="8663f-113">For more information about specifying device information settings for a render operation, and to view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a><span data-ttu-id="8663f-114">尋找及修改 RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="8663f-114">Finding and Modifying RSReportServer.config</span></span>  
 <span data-ttu-id="8663f-115">報表輸出格式的組態設定會在 RSReportServer.config 檔中指定為轉譯延伸模組參數。</span><span class="sxs-lookup"><span data-stu-id="8663f-115">Configuration settings for report output formats are specified as rendering extension parameters in the RSReportServer.config file.</span></span> <span data-ttu-id="8663f-116">若要指定組態檔中的轉譯延伸模組參數，您必須了解如何定義設定轉譯參數的 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="8663f-116">To specify rendering extension parameters in the configuration files, you must know how to define the XML structures that set rendering parameters.</span></span> <span data-ttu-id="8663f-117">可進行修改的 XML 結構有兩種：</span><span class="sxs-lookup"><span data-stu-id="8663f-117">There are two XML structures that you can modify:</span></span>  
  
-   <span data-ttu-id="8663f-118">`OverrideNames` 元素會定義轉譯延伸模組顯示的名稱和語言。</span><span class="sxs-lookup"><span data-stu-id="8663f-118">The `OverrideNames` element defines the display name and language of the rendering extension.</span></span>  
  
-   <span data-ttu-id="8663f-119">`DeviceInfo` XML 結構會定義轉譯延伸模組所使用的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8663f-119">The `DeviceInfo` XML structure defines the device information settings that are used by a rendering extension.</span></span> <span data-ttu-id="8663f-120">大部分的轉譯延伸模組參數會指定為裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8663f-120">Most rendering extension parameters are specified as device information settings.</span></span>  
  
 <span data-ttu-id="8663f-121">您可以使用文字編輯器來修改 RSReportServer.config 檔案，</span><span class="sxs-lookup"><span data-stu-id="8663f-121">You can use a text editor to modify the file.</span></span> <span data-ttu-id="8663f-122">此檔案可以在 \Reporting Services\Report Server\Bin 資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="8663f-122">The RSReportServer.config file can be found in the \Reporting Services\Report Server\Bin folder.</span></span> <span data-ttu-id="8663f-123">如需修改設定檔的詳細資訊，請參閱[修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="8663f-123">For more information about modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span>  
  
## <a name="changing-the-display-name"></a><span data-ttu-id="8663f-124">變更顯示名稱</span><span class="sxs-lookup"><span data-stu-id="8663f-124">Changing the Display Name</span></span>  
 <span data-ttu-id="8663f-125">轉譯延伸模組的顯示名稱會出現在報表工具列的 [匯出] 清單中。</span><span class="sxs-lookup"><span data-stu-id="8663f-125">The display name for a rendering extension appears in the Export list of the report toolbar.</span></span> <span data-ttu-id="8663f-126">預設顯示名稱的範例包括網頁封存、TIFF 檔案和 Acrobat (PDF) 檔案。</span><span class="sxs-lookup"><span data-stu-id="8663f-126">Examples of default display names include Web archive, TIFF file, and Acrobat (PDF) file.</span></span> <span data-ttu-id="8663f-127">藉著指定組態檔中的 `OverrideNames` 元素，您可以使用自訂的值來取代預設的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8663f-127">You can replace the default display name with a custom value by specifying the `OverrideNames` element in the configuration files.</span></span> <span data-ttu-id="8663f-128">此外，如果您正在定義單一轉譯延伸模組的兩個執行個體，也可以使用 `OverrideNames` 元素在 [匯出] 清單中區分每一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8663f-128">In addition, if you are defining two instances of a single rendering extension, you can use the `OverrideNames` element to distinguish each instance in the Export list.</span></span>  
  
 <span data-ttu-id="8663f-129">由於顯示名稱已經當地語系化，如果您要使用自訂的值取代預設顯示名稱，就必須設定 `Language` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8663f-129">Because display names are localized, you must set the `Language` attribute if you are replacing the default display name with a custom value.</span></span> <span data-ttu-id="8663f-130">否則，任何指定的名稱都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="8663f-130">Otherwise, any name that you specify will be ignored.</span></span> <span data-ttu-id="8663f-131">您所設定的語言值，對於報表伺服器電腦必須是有效值。</span><span class="sxs-lookup"><span data-stu-id="8663f-131">The language value that you set must be valid for the report server computer.</span></span> <span data-ttu-id="8663f-132">例如，如果報表伺服器是在法文作業系統上執行，您應該指定「fr-FR」做為屬性值。</span><span class="sxs-lookup"><span data-stu-id="8663f-132">For example, if the report server is running on a French operating system, you should specify "fr-FR" as the attribute value.</span></span>  
  
 <span data-ttu-id="8663f-133">下列範例會說明在英文報表伺服器上提供自訂名稱的方法：</span><span class="sxs-lookup"><span data-stu-id="8663f-133">The following example illustrates how to provide a custom name on an English report server:</span></span>  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a><span data-ttu-id="8663f-134">變更裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="8663f-134">Changing Device Information Settings</span></span>  
 <span data-ttu-id="8663f-135">若要修改已經部署在您報表伺服器上之轉譯延伸模組所使用的預設裝置資訊設定，您必須在組態檔中輸入 `DeviceInfo` XML 結構。</span><span class="sxs-lookup"><span data-stu-id="8663f-135">To modify default device information settings that are used by a rendering extension that is already deployed on your report server, you must type the `DeviceInfo` XML structure into the configuration files.</span></span> <span data-ttu-id="8663f-136">每一個轉譯延伸模組都支援該延伸模組獨特的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8663f-136">Every rendering extension supports device information settings that are unique to that extension.</span></span> <span data-ttu-id="8663f-137">若要檢視裝置資訊設定的完整清單，請參閱 [將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="8663f-137">To view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="8663f-138">下列範例會提供 XML 結構的說明，以及修改影像轉譯延伸模組預設設定的語法：</span><span class="sxs-lookup"><span data-stu-id="8663f-138">The following example provides an illustration of the XML structure and syntax that modifies the default settings of the Image rendering extension:</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a><span data-ttu-id="8663f-139">設定轉譯延伸模組的多個項目</span><span class="sxs-lookup"><span data-stu-id="8663f-139">Configuring Multiple Entries for a Rendering Extension</span></span>  
 <span data-ttu-id="8663f-140">您可以建立同一個轉譯延伸模組的多個執行個體，以支援不同的報表呈現選項。</span><span class="sxs-lookup"><span data-stu-id="8663f-140">You can create multiple instances of the same rendering extension to support different report presentation options.</span></span> <span data-ttu-id="8663f-141">您定義的每個執行個體可以具有不同的參數值組合。</span><span class="sxs-lookup"><span data-stu-id="8663f-141">Each instance that you define can have a different combination of parameter values.</span></span> <span data-ttu-id="8663f-142">定義現有轉譯延伸模組的執行個體時，請務必執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8663f-142">When defining new instances of an existing rendering extension, be sure to do the following:</span></span>  
  
-   <span data-ttu-id="8663f-143">指定延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8663f-143">Specify a unique name for the extension.</span></span>  
  
     <span data-ttu-id="8663f-144">每個延伸模組必須具有 `Name` 屬性的唯一值。</span><span class="sxs-lookup"><span data-stu-id="8663f-144">Each instance must have a unique value for the `Name` attribute.</span></span> <span data-ttu-id="8663f-145">下列範例會使用 "IMAGE (EMF Landscape)" 和 "IMAGE (EMF Portrait)" 的名稱來區分兩個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8663f-145">The following example uses the names "IMAGE (EMF Landscape)" and "IMAGE (EMF Portrait)" to distinguish between the two instances.</span></span>  
  
     <span data-ttu-id="8663f-146">變更已經部署之轉譯延伸模組的名稱時，要特別小心，</span><span class="sxs-lookup"><span data-stu-id="8663f-146">Use caution when changing the name of a rendering extension that is already deployed.</span></span> <span data-ttu-id="8663f-147">因為透過程式設計的方式指定轉譯延伸模組的開發人員，會使用延伸模組名稱來識別特定轉譯作業所使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8663f-147">Developers who specify rendering extensions programmatically use the extension name to identify which instance to use for a particular render operation.</span></span> <span data-ttu-id="8663f-148">如果您在報表伺服器上執行自訂的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 應用程式，請確定開發人員知道您修改了現有的延伸模組名稱，或是新增了新的延伸模組名稱。</span><span class="sxs-lookup"><span data-stu-id="8663f-148">If you are running custom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applications on your report server, make sure that the developer knows if you modify an existing extension name or add a new one.</span></span>  
  
-   <span data-ttu-id="8663f-149">請指定唯一的顯示名稱，如此使用者可以了解每一個輸出格式的差異。</span><span class="sxs-lookup"><span data-stu-id="8663f-149">Specify a unique display name so that users can understand the differences for each output format.</span></span>  
  
     <span data-ttu-id="8663f-150">如果您為同一個延伸模組設定多個版本，則可以提供 `OverrideNames` 的值，藉此為每個版本指定一個唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8663f-150">If you are configuring multiple versions of the same extension, you can give each version a unique name by providing a value for `OverrideNames`.</span></span> <span data-ttu-id="8663f-151">否則，在報表工具列的 [匯出] 清單中，每個版本的延伸模組都會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8663f-151">Otherwise, all versions of the extension will appear to have the same name in the Export options list on the report toolbar.</span></span>  
  
 <span data-ttu-id="8663f-152">下列範例說明使用預設影像轉譯延伸模組 (這會產生 TIFF 輸出) 輸出縱向模式 EMF，連同以第二個執行個體輸出橫向模式 EMF 格式報表的方法。</span><span class="sxs-lookup"><span data-stu-id="8663f-152">The following example illustrates how to use the default Image rendering extension (which produces TIFF output) to output EMF in Portrait mode alongside a second instance that outputs reports in EMF in Landscape mode.</span></span> <span data-ttu-id="8663f-153">請注意，每個延伸模組名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8663f-153">Notice that each extension name is unique.</span></span> <span data-ttu-id="8663f-154">測試此範例時，請記得選擇沒有包含互動式功能 (例如顯示/隱藏選項、矩陣或鑽研連結) 的報表，因為互動式功能不能在影像轉譯延伸模組中執行：</span><span class="sxs-lookup"><span data-stu-id="8663f-154">When testing this example, remember to choose reports that do not contain interactive features such as show/hide options, matrices, or drillthrough links (interactive features do not work in the Image rendering extension):</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8663f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8663f-155">See Also</span></span>  
 <span data-ttu-id="8663f-156">[Rsreportserver.config 設定檔](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-156">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="8663f-157">[RSReportDesigner 組態檔](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-157">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="8663f-158">[CSV 裝置資訊設定](csv-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-158">[CSV Device Information Settings](csv-device-information-settings.md) </span></span>  
 <span data-ttu-id="8663f-159">[Excel 裝置資訊設定](excel-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-159">[Excel Device Information Settings](excel-device-information-settings.md) </span></span>  
 <span data-ttu-id="8663f-160">[HTML 裝置資訊設定](html-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-160">[HTML Device Information Settings](html-device-information-settings.md) </span></span>  
 <span data-ttu-id="8663f-161">[影像裝置資訊設定](image-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-161">[Image Device Information Settings](image-device-information-settings.md) </span></span>  
 <span data-ttu-id="8663f-162">[MHTML 裝置資訊設定](mhtml-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-162">[MHTML Device Information Settings](mhtml-device-information-settings.md) </span></span>  
 <span data-ttu-id="8663f-163">[PDF 裝置資訊設定](pdf-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="8663f-163">[PDF Device Information Settings](pdf-device-information-settings.md) </span></span>  
 [<span data-ttu-id="8663f-164">XML 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="8663f-164">XML Device Information Settings</span></span>](xml-device-information-settings.md)  
  
  
