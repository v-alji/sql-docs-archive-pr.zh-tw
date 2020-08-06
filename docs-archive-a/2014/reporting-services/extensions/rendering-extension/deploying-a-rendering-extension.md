---
title: 部署轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1c70d9cdc947134c682132b0baea02274ddf4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596535"
---
# <a name="deploying-a-rendering-extension"></a><span data-ttu-id="9601c-102">部署轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="9601c-102">Deploying a Rendering Extension</span></span>
  <span data-ttu-id="9601c-103">在您撰寫 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 報表轉譯延伸模組並將其編譯成 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程式庫之後，需要使其可供報表伺服器和報表設計師探索。</span><span class="sxs-lookup"><span data-stu-id="9601c-103">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report rendering extension into a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="9601c-104">若要這樣做，請將延伸模組複製到適當的目錄，並將項目加入適當的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態檔。</span><span class="sxs-lookup"><span data-stu-id="9601c-104">To do so, copy the extension to the appropriate directory and add entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-rendering-extension-element"></a><span data-ttu-id="9601c-105">組態檔轉譯延伸模組元素</span><span class="sxs-lookup"><span data-stu-id="9601c-105">Configuration File Rendering Extension Element</span></span>  
 <span data-ttu-id="9601c-106">在將轉譯延伸模組編譯成 .DLL 之後，您就可以將項目加入至 rsreportserver.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="9601c-106">Once a rendering extension has been compiled into a .DLL, you add an entry into the rsreportserver.config file.</span></span> <span data-ttu-id="9601c-107">根據預設，位置為%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="9601c-107">By default, the location is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="9601c-108">父項目為 \<Render>。</span><span class="sxs-lookup"><span data-stu-id="9601c-108">The parent element is \<Render>.</span></span> <span data-ttu-id="9601c-109">Render 元素之下是代表每個轉譯延伸模組的 Extension 元素。</span><span class="sxs-lookup"><span data-stu-id="9601c-109">Under the Render element is an Extension element for each rendering extension.</span></span> <span data-ttu-id="9601c-110">`Extension` 元素包含兩個屬性：Name 與 Type。</span><span class="sxs-lookup"><span data-stu-id="9601c-110">The `Extension` element contains two attributes, Name and Type.</span></span>  
  
 <span data-ttu-id="9601c-111">下表描述用於轉譯延伸模組之 `Extension` 元素的屬性：</span><span class="sxs-lookup"><span data-stu-id="9601c-111">The following table describes the attributes for the `Extension` element for rendering extensions:</span></span>  
  
|<span data-ttu-id="9601c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9601c-112">Attribute</span></span>|<span data-ttu-id="9601c-113">描述</span><span class="sxs-lookup"><span data-stu-id="9601c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9601c-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="9601c-114">**Name**</span></span>|<span data-ttu-id="9601c-115">延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9601c-115">A unique name for the extension.</span></span> <span data-ttu-id="9601c-116">**Name** 屬性的最大長度為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="9601c-116">The maximum length for the **Name** attribute is 255 characters.</span></span> <span data-ttu-id="9601c-117">該名稱在組態檔之 **Extensions** 元素的所有項目中，必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9601c-117">The name must be unique among all entries within the **Extensions** element of a configuration file.</span></span> <span data-ttu-id="9601c-118">如果重複的名稱存在，報表伺服器會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9601c-118">If a duplicate name is present, the report server returns an error.</span></span>|  
|<span data-ttu-id="9601c-119">**型別**</span><span class="sxs-lookup"><span data-stu-id="9601c-119">**Type**</span></span>|<span data-ttu-id="9601c-120">以逗號分隔的清單，包括完整的命名空間以及組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9601c-120">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|<span data-ttu-id="9601c-121">**Visible**</span><span class="sxs-lookup"><span data-stu-id="9601c-121">**Visible**</span></span>|<span data-ttu-id="9601c-122">值若為 `false` 表示轉譯延伸模組不應該顯示在使用者介面中。</span><span class="sxs-lookup"><span data-stu-id="9601c-122">A value of `false` indicates that the rendering extension should not be visible in user interfaces.</span></span> <span data-ttu-id="9601c-123">如果沒有包括屬性，預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="9601c-123">If the attribute is not included, the default value is `true`.</span></span>|  
|<span data-ttu-id="9601c-124">**LogAllExecutionRequests**</span><span class="sxs-lookup"><span data-stu-id="9601c-124">**LogAllExecutionRequests**</span></span>|<span data-ttu-id="9601c-125">值若為 `false` 表示只會針對工作階段中的第一項報表執行作業記錄項目。</span><span class="sxs-lookup"><span data-stu-id="9601c-125">A value of `false` indicates that an entry is logged for only the first report execution in a session.</span></span> <span data-ttu-id="9601c-126">如果沒有包括屬性，預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="9601c-126">If the attribute is not included, the default value is `true`.</span></span><br /><br /> <span data-ttu-id="9601c-127">例如，這項設定會決定只針對報表中轉譯的第一個頁面記錄項目 (當此值為 `false` 時)，還是針對報表中轉譯的每個頁面記錄項目 (當此值為 `true` 時)。</span><span class="sxs-lookup"><span data-stu-id="9601c-127">For example, this setting determines whether to log an entry for only the first page rendered in a report (when `false`) or an entry for each page rendered in the report (when `true`).</span></span>|  
  
 <span data-ttu-id="9601c-128">如需詳細資訊，請參閱 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="9601c-128">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="9601c-129">將延伸模組部署到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="9601c-129">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="9601c-130">報表伺服器會使用轉譯延伸模組將報表匯出成其他格式。</span><span class="sxs-lookup"><span data-stu-id="9601c-130">The report server uses rendering extensions to export reports to other formats.</span></span> <span data-ttu-id="9601c-131">您應該將轉譯延伸模組組件部署到報表伺服器做為私用組件。</span><span class="sxs-lookup"><span data-stu-id="9601c-131">You should deploy your rendering extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="9601c-132">也需要在報表伺服器組態檔 rsreportserver.config 中建立項目。</span><span class="sxs-lookup"><span data-stu-id="9601c-132">You also need to make an entry in the report server configuration file, rsreportserver.config.</span></span>  
  
### <a name="to-deploy-the-assembly"></a><span data-ttu-id="9601c-133">若要部署組件</span><span class="sxs-lookup"><span data-stu-id="9601c-133">To deploy the assembly</span></span>  
  
1.  <span data-ttu-id="9601c-134">將組件從執行位置複製到您要在其上使用轉譯延伸模組之報表伺服器的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="9601c-134">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the rendering extension.</span></span> <span data-ttu-id="9601c-135">報表伺服器 Bin 目錄的預設位置是%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="9601c-135">The default location of the report server Bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\Bin.</span></span>  
  
2.  <span data-ttu-id="9601c-136">在複製組件檔之後，開啟 rsreportserver.config 檔。</span><span class="sxs-lookup"><span data-stu-id="9601c-136">After the assembly file is copied, open the rsreportserver.config file.</span></span> <span data-ttu-id="9601c-137">rsreportserver.config 檔也位於報表伺服器的 bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="9601c-137">The rsreportserver.config file is also located in the report server bin directory.</span></span> <span data-ttu-id="9601c-138">您需要在延伸模組組件檔的組態檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="9601c-138">You need to make an entry in the configuration file for your extension assembly file.</span></span> <span data-ttu-id="9601c-139">您可以利用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="9601c-139">You can open the file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor.</span></span>  
  
     <span data-ttu-id="9601c-140">如需詳細資訊，請參閱 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="9601c-140">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
3.  <span data-ttu-id="9601c-141">在 Rsreportserver.config 檔中，找出 **Render** 元素。</span><span class="sxs-lookup"><span data-stu-id="9601c-141">Locate the **Render** element in the Rsreportserver.config file.</span></span> <span data-ttu-id="9601c-142">應該針對您新建立的延伸模組，在下列位置建立項目：</span><span class="sxs-lookup"><span data-stu-id="9601c-142">An entry for your newly created extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="9601c-143">針對您的傳遞延伸模組加入項目。</span><span class="sxs-lookup"><span data-stu-id="9601c-143">Add an entry for your rendering extension.</span></span> <span data-ttu-id="9601c-144">您的項目應該包含具有 **Name** 和 **Type**值的元素，且看起來可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="9601c-144">Your entry should include an element that has values for **Name** and **Type**, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     <span data-ttu-id="9601c-145">**Name** 值是轉譯延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9601c-145">The value for **Name** is the unique name of the rendering extension.</span></span> <span data-ttu-id="9601c-146">**類型**的值是以逗號分隔的清單，包括 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 實作的完整命名空間項目，後面接著組件的名稱 (不包括 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="9601c-146">The value for **Type** is a comma-separated list that includes an entry for the fully qualified namespace of your <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> implementation, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="9601c-147">根據預設，轉譯延伸模組是可見的。</span><span class="sxs-lookup"><span data-stu-id="9601c-147">By default, rendering extensions are visible.</span></span> <span data-ttu-id="9601c-148">若要隱藏使用者介面的擴充功能（例如報表管理員），請將**Visible**屬性加入至專案 `Extension` ，並將其設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9601c-148">To hide an extension from user interfaces, such as Report Manager, add a **Visible** attribute to the `Extension` element, and set it to `false`.</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="9601c-149">確認部署</span><span class="sxs-lookup"><span data-stu-id="9601c-149">Verifying the deployment</span></span>  
 <span data-ttu-id="9601c-150">您也可以開啟報表管理員，然後確認延伸模組是否包含在報表可用匯出類型的清單中。</span><span class="sxs-lookup"><span data-stu-id="9601c-150">You can also open Report Manager and verify that your extension is included in the list of available export types for a report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9601c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9601c-151">See Also</span></span>  
 <span data-ttu-id="9601c-152">[實作轉譯延伸模組](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="9601c-152">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="9601c-153">[轉譯延伸模組概觀](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="9601c-153">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="9601c-154">[實作 IRenderingExtension 介面](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="9601c-154">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 [<span data-ttu-id="9601c-155">延伸模組的安全性考量</span><span class="sxs-lookup"><span data-stu-id="9601c-155">Security Considerations for Extensions</span></span>](../security-considerations-for-extensions.md)  
  
  
