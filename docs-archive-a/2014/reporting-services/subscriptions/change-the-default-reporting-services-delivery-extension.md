---
title: 變更預設 Reporting Services 傳遞延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703753"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a><span data-ttu-id="279ea-102">變更預設 Reporting Services 傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="279ea-102">Change the Default Reporting Services Delivery Extension</span></span>
  <span data-ttu-id="279ea-103">您可以修改 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態設定，以變更訂閱定義頁面的 **[傳遞者]** 清單中所顯示的預設傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="279ea-103">You can modify [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration settings to change the default delivery extension that appears in the **Delivered by** list of a subscription definition page.</span></span> <span data-ttu-id="279ea-104">例如，您可以修改組態，使得在使用者建立新的訂閱時依預設會選取檔案共用傳遞，而不是電子郵件傳遞。</span><span class="sxs-lookup"><span data-stu-id="279ea-104">For example you can modify the configuration so that when users create a new subscription, file share delivery is selected by default instead of e-mail delivery.</span></span> <span data-ttu-id="279ea-105">您也可以變更傳遞延伸模組在使用者介面中列出的順序。</span><span class="sxs-lookup"><span data-stu-id="279ea-105">You can also change the order the delivery extensions are listed in the user interface.</span></span>

 <span data-ttu-id="279ea-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="279ea-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="279ea-107">包含電子郵件和 Windows 檔案共用傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="279ea-107">includes E-mail and Windows File Share delivery are extensions.</span></span> <span data-ttu-id="279ea-108">如果您部署了自訂或協力廠商延伸模組來支援自訂傳遞，那麼報表伺服器可能會有其他的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="279ea-108">Your report server might have additional delivery extensions if you have deployed custom or third-party extensions to support custom delivery.</span></span> <span data-ttu-id="279ea-109">傳遞延伸模組是否可用取決於該模組是否部署於報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="279ea-109">The availability of a delivery extension depends on whether it is deployed on a report server.</span></span>

## <a name="default-native-mode-report-server-configuration"></a><span data-ttu-id="279ea-110">預設原生模式報表伺服器組態</span><span class="sxs-lookup"><span data-stu-id="279ea-110">Default Native mode report server configuration</span></span>
 <span data-ttu-id="279ea-111">在 **[傳遞者]** 清單的 [報表管理員] 中顯示傳遞延伸模組的順序，是根據 **RSReportServer.config** 檔中傳遞延伸模組項目的順序而定。</span><span class="sxs-lookup"><span data-stu-id="279ea-111">The order of a delivery extension appears in Report Manager in the **Delivered by** list is based on the order of the delivery extension entries in the **RSReportServer.config** file.</span></span> <span data-ttu-id="279ea-112">例如，下圖在清單中會先顯示電子郵件，並依預設加以選取。</span><span class="sxs-lookup"><span data-stu-id="279ea-112">For example the following image shows e-mail first in the list and it is selected by default.</span></span>

 <span data-ttu-id="279ea-113">![預設的傳遞延伸模組清單](../media/ssrs-default-delivery.png "預設的傳遞延伸模組清單")</span><span class="sxs-lookup"><span data-stu-id="279ea-113">![default list of delivery extensions](../media/ssrs-default-delivery.png "default list of delivery extensions")</span></span>

 <span data-ttu-id="279ea-114">以下是 **RSReportServer.config** 的預設區段，會控制預設傳遞延伸模組及其在報表管理員中的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="279ea-114">The following is the default section of **RSReportServer.config** that controls the default delivery extension and the order they are displayed in Report Manager.</span></span> <span data-ttu-id="279ea-115">請注意，電子郵件會先出現在檔案中，並且設為預設值。</span><span class="sxs-lookup"><span data-stu-id="279ea-115">Note that email appears first in the file and it is set as the default.</span></span>

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a><span data-ttu-id="279ea-116">將檔案共用傳遞設定為報表管理員中的預設傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="279ea-116">Configure File Share Delivery as the default delivery extension in Report Manager</span></span>

1.  <span data-ttu-id="279ea-117">此程序中的步驟會修改組態，讓檔案共用傳遞列示為 UI 中的第一個選項，並且是預設選取項目。</span><span class="sxs-lookup"><span data-stu-id="279ea-117">The steps in this procedure modify the configuration so that file share delivery is listed as the first option in the UI and it is the default selection.</span></span>

     <span data-ttu-id="279ea-118">在文字編輯器中開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="279ea-118">Open the RSReportServer.config file in a text editor.</span></span> <span data-ttu-id="279ea-119">如需組態檔的詳細資訊，請參閱＜ [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)＞。</span><span class="sxs-lookup"><span data-stu-id="279ea-119">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span> <span data-ttu-id="279ea-120">組態變更之後，UI 會如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="279ea-120">After the configuration changes, the UI will look like the following image:</span></span>

     <span data-ttu-id="279ea-121">![修改過的傳遞延伸模組清單](../media/ssrs-modified-delivery.png "修改過的傳遞延伸模組清單")</span><span class="sxs-lookup"><span data-stu-id="279ea-121">![modified list of delivery extensions](../media/ssrs-modified-delivery.png "modified list of delivery extensions")</span></span>

2.  <span data-ttu-id="279ea-122">修改 DeliveryUI 區段使其如下列範例所示，並記下主要變更：</span><span class="sxs-lookup"><span data-stu-id="279ea-122">Modify the DeliveryUI section to look like the following sample and note the key changes of:</span></span>

    1.  <span data-ttu-id="279ea-123">FileShare 延伸模組位於電子郵件延伸模組之前。</span><span class="sxs-lookup"><span data-stu-id="279ea-123">The FileShare extension is before the email extension.</span></span> <span data-ttu-id="279ea-124">這會變更延伸模組在報表管理員中的列出順序。</span><span class="sxs-lookup"><span data-stu-id="279ea-124">This will change the order the extensions are listed in Report Manager.</span></span>

    2.  <span data-ttu-id="279ea-125">檔案共用延伸模組包含 DefaultExtension 標記 `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` ，且延伸模組結束標記已加上 `</Extension>`。</span><span class="sxs-lookup"><span data-stu-id="279ea-125">The File share extension contains DefaultExtension tag `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` and the extension end tag was added `</Extension>`.</span></span>

    3.  <span data-ttu-id="279ea-126">電子郵件延伸模組不再設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="279ea-126">The email extension is no longer configured as the default.</span></span> `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  <span data-ttu-id="279ea-127">儲存組態檔。</span><span class="sxs-lookup"><span data-stu-id="279ea-127">Save the configuration file.</span></span>

4.  <span data-ttu-id="279ea-128">在幾分鐘內，報表伺服器即會重新載入組態檔，且新設定將會生效。</span><span class="sxs-lookup"><span data-stu-id="279ea-128">Within a few minutes the report server will reload the configuration file and the new settings will take effect.</span></span> <span data-ttu-id="279ea-129">您可以重新啟動報表伺服器服務，以強制載入組態檔。</span><span class="sxs-lookup"><span data-stu-id="279ea-129">You can restart the report server service to force the loading of the configuration file.</span></span>

     <span data-ttu-id="279ea-130">在讀取組態時，下列事件會寫入至 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="279ea-130">The following event is written to the windows event log when the configuration is read.</span></span>

     <span data-ttu-id="279ea-131">**事件識別碼：** 109</span><span class="sxs-lookup"><span data-stu-id="279ea-131">**Event ID:** 109</span></span>

     <span data-ttu-id="279ea-132">**來源：** 報表伺服器 Windows 服務 (執行個體名稱)</span><span class="sxs-lookup"><span data-stu-id="279ea-132">**Source:** Report Server Windows Service (instance name)</span></span>

     <span data-ttu-id="279ea-133">已修改 RSReportServer.config 檔</span><span class="sxs-lookup"><span data-stu-id="279ea-133">The RSReportServer.config file has been modified</span></span>

## <a name="sharepoint-mode-report-servers"></a><span data-ttu-id="279ea-134">SharePoint 模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="279ea-134">SharePoint mode report servers</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="279ea-135">SharePoint 模式會在 SharePoint 服務應用程式資料庫中儲存延伸模組資訊，而不是在 RsrReportServer.config 檔中儲存。</span><span class="sxs-lookup"><span data-stu-id="279ea-135">SharePoint mode stores extensions information in the SharePoint service application databases and not in the RsrReportServer.config file.</span></span> <span data-ttu-id="279ea-136">在 SharePoint 模式中，傳遞延伸模組組態會使用 PowerShell 進行修改。</span><span class="sxs-lookup"><span data-stu-id="279ea-136">In SharePoint mode, delivery extension configuration is modified using PowerShell.</span></span>

#### <a name="configure-the-default-delivery-extension"></a><span data-ttu-id="279ea-137">設定預設傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="279ea-137">Configure the default delivery extension</span></span>

1.  <span data-ttu-id="279ea-138">開啟 **[SharePoint 管理命令介面]** 。</span><span class="sxs-lookup"><span data-stu-id="279ea-138">Open the **SharePoint Management Shell**.</span></span>

2.  <span data-ttu-id="279ea-139">如果您已知道 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務應用程式的名稱，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="279ea-139">You can skip this step if you already know the name of your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="279ea-140">使用下列 PowerShell，列出您 SharePoint 伺服器陣列中的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="279ea-140">Use the following PowerShell to list the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service applications in your SharePoint farm.</span></span>

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  <span data-ttu-id="279ea-141">執行下列 PowerShell，以驗證 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務應用程式 "ssrsapp" 目前的預設傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="279ea-141">Run the following PowerShell to verify the current default delivery extension for the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application "ssrsapp".</span></span>

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a><span data-ttu-id="279ea-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="279ea-142">See Also</span></span>
 <span data-ttu-id="279ea-143">[Rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md) [rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md)案[共用傳遞 Reporting Services](file-share-delivery-in-reporting-services.md)的[電子郵件傳遞 Reporting Services](e-mail-delivery-in-reporting-services.md) [設定報表伺服器以進行電子郵件傳遞 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="279ea-143">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span></span>
