---
title: 部署傳遞延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4a4e33266c8d3a27ce2a4ab5f568bdee349720f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607293"
---
# <a name="deploying-a-delivery-extension"></a><span data-ttu-id="d0c67-102">部署傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="d0c67-102">Deploying a Delivery Extension</span></span>
  <span data-ttu-id="d0c67-103">傳遞延伸模組以 XML 組態檔的形式提供其組態資訊。</span><span class="sxs-lookup"><span data-stu-id="d0c67-103">Delivery extensions supply their configuration information in the form of an XML configuration file.</span></span> <span data-ttu-id="d0c67-104">XML 檔案符合為傳遞延伸模組定義的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0c67-104">The XML file conforms to the XML schema defined for delivery extensions.</span></span> <span data-ttu-id="d0c67-105">傳遞延伸模組提供設定和修改組態檔的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d0c67-105">Delivery extensions provide infrastructure for setting and modifying the configuration file.</span></span>  
  
 <span data-ttu-id="d0c67-106">如果取代或升級傳遞延伸模組，則所有參考傳遞延伸模組的訂閱仍然會有效。</span><span class="sxs-lookup"><span data-stu-id="d0c67-106">If a delivery extension is replaced or upgraded, all subscriptions that reference the delivery extension remain valid.</span></span>  
  
 <span data-ttu-id="d0c67-107">在您將 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組撰寫和編譯成 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程式庫之後，必須將延伸模組複製到適當的目錄，並將項目新增至適當的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 設定檔，這樣報表伺服器就可以找到它。</span><span class="sxs-lookup"><span data-stu-id="d0c67-107">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you must copy the extension to the appropriate directory and add an entry to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration file so the report server can locate it.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="d0c67-108">組態檔延伸模組元素</span><span class="sxs-lookup"><span data-stu-id="d0c67-108">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="d0c67-109">部署到報表伺服器的傳遞延伸模組，需要在組態檔中輸入成 `Extension` 元素。</span><span class="sxs-lookup"><span data-stu-id="d0c67-109">Delivery extensions that you deploy to the report server need to be entered as `Extension` elements in the configuration file.</span></span> <span data-ttu-id="d0c67-110">報表伺服器的組態檔是 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="d0c67-110">The configuration file for the report server is RSReportServer.config.</span></span>  
  
 <span data-ttu-id="d0c67-111">下表說明傳遞延伸模組之 `Extension` 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="d0c67-111">The following table describes the attributes for the `Extension` element for delivery extensions.</span></span>  
  
|<span data-ttu-id="d0c67-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d0c67-112">Attribute</span></span>|<span data-ttu-id="d0c67-113">描述</span><span class="sxs-lookup"><span data-stu-id="d0c67-113">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="d0c67-114">延伸模組的唯一名稱 (例如，供電子郵件傳遞延伸模組使用的 "Report Server E-Mail"，或是供檔案共用傳遞延伸模組使用的 "Report Server FileShare")。</span><span class="sxs-lookup"><span data-stu-id="d0c67-114">A unique name for the extension (for example, "Report Server E-Mail" for the e-mail delivery extension or "Report Server FileShare" for the file share delivery extension).</span></span> <span data-ttu-id="d0c67-115">`Name` 屬性的最大長度為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="d0c67-115">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="d0c67-116">該名稱在組態檔之 `Extension` 元素的所有元素中，必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d0c67-116">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="d0c67-117">如果重複的名稱存在，報表伺服器會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0c67-117">If a duplicate name is present, the report server returns an error.</span></span>|  
|`Type`|<span data-ttu-id="d0c67-118">以逗號分隔的清單，包括完整的命名空間以及組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c67-118">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="d0c67-119">`false` 值指出在使用者介面中應該看不到傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d0c67-119">A value of `false` indicates that the delivery extension should not be visible in user interfaces.</span></span> <span data-ttu-id="d0c67-120">如果沒有包括屬性，預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="d0c67-120">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="d0c67-121">如需 RSReportServer.config 或 RSReportDesigner.config 檔的詳細資訊，請參閱 [Reporting Services 設定檔](../../report-server/reporting-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="d0c67-121">For more information about the RSReportServer.config file, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="d0c67-122">將延伸模組部署到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="d0c67-122">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="d0c67-123">報表伺服器使用傳遞延伸模組來處理和傳遞通知或是報表。</span><span class="sxs-lookup"><span data-stu-id="d0c67-123">The report server uses delivery extensions for processing and delivering notifications or reports.</span></span> <span data-ttu-id="d0c67-124">您應該將傳遞延伸模組組件部署到報表伺服器做為私用組件，</span><span class="sxs-lookup"><span data-stu-id="d0c67-124">You should deploy your delivery extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="d0c67-125">也需要在報表伺服器組態檔 RSReportServer.config 中建立項目。</span><span class="sxs-lookup"><span data-stu-id="d0c67-125">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a><span data-ttu-id="d0c67-126">將傳遞延伸模組組件部署到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="d0c67-126">To deploy a deliver extension assembly to a report server</span></span>  
  
1.  <span data-ttu-id="d0c67-127">將組件從執行位置複製到您要在其上使用傳遞延伸模組之報表伺服器的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="d0c67-127">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the delivery extension.</span></span> <span data-ttu-id="d0c67-128">報表伺服器 bin 目錄的預設位置是%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="d0c67-128">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d0c67-129">如果您嘗試覆寫現有的傳遞延伸模組件，必須先停止報表伺服器服務，再複製更新的組件。</span><span class="sxs-lookup"><span data-stu-id="d0c67-129">If you are attempting to overwrite an existing delivery extension assembly, you must first stop the Report Server service before copying the updated assembly.</span></span> <span data-ttu-id="d0c67-130">在組件完成複製之後，重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="d0c67-130">Restart your service after the assembly is through copying.</span></span>  
  
2.  <span data-ttu-id="d0c67-131">在複製組件檔之後，開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="d0c67-131">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="d0c67-132">RSReportServer.config 檔案位於%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\ReportServer 目錄。</span><span class="sxs-lookup"><span data-stu-id="d0c67-132">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="d0c67-133">您需要在傳遞延伸模組組件檔的組態檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="d0c67-133">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="d0c67-134">您可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器（例如 [記事本]）開啟設定檔。</span><span class="sxs-lookup"><span data-stu-id="d0c67-134">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="d0c67-135">在 RSReportServer.config 檔中，找出 `Delivery` 元素。</span><span class="sxs-lookup"><span data-stu-id="d0c67-135">Locate the `Delivery` element in the RSReportServer.config file.</span></span> <span data-ttu-id="d0c67-136">應該針對您新建立的傳遞延伸模組，在下列位置建立項目：</span><span class="sxs-lookup"><span data-stu-id="d0c67-136">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="d0c67-137">針對您的傳遞延伸模組加入項目。</span><span class="sxs-lookup"><span data-stu-id="d0c67-137">Add an entry for your delivery extension.</span></span> <span data-ttu-id="d0c67-138">您的項目應該包含具有 `Extension` 和 `Name` 值的 `Type` 元素，且可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c67-138">Your entry should include an `Extension` element with values for `Name` and `Type`, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="d0c67-139">`Name` 的值是傳遞延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c67-139">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="d0c67-140">`Type` 的值是以逗號分隔的清單，包括實作 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 介面之類別的完整命名空間項目，後面接著組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="d0c67-140">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="d0c67-141">依預設，傳遞延伸模組是可見的。</span><span class="sxs-lookup"><span data-stu-id="d0c67-141">By default, delivery extensions are visible.</span></span> <span data-ttu-id="d0c67-142">若要在使用者介面中隱藏延伸模組 (例如報表管理員)，請將 `Visible` 屬性加入至 `Extension` 元素，並將其設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d0c67-142">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="d0c67-143">最後，針對為傳遞延伸模組授與 `FullTrust` 權限的自訂組件，加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="d0c67-143">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="d0c67-144">若要這麼做，您可以將程式碼群組加入至預設位於%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 中的 rssrvpolicy.config 檔案。 \<InstanceName>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="d0c67-144">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="d0c67-145">您的程式碼群組可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c67-145">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="d0c67-146">URL 成員資格僅是您可以針對傳遞延伸模組所選擇的許多成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="d0c67-146">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="d0c67-147">如需 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 程式碼存取安全性的詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="d0c67-147">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see.[Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="deploying-the-extension-to-report-manager"></a><span data-ttu-id="d0c67-148">將延伸模組部署到報表管理員</span><span class="sxs-lookup"><span data-stu-id="d0c67-148">Deploying the Extension to Report Manager</span></span>  
 <span data-ttu-id="d0c67-149">如果您的傳遞延伸模組實作 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 介面，就可以將傳遞延伸模組與報表管理員的 [訂閱] 頁面搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d0c67-149">If your delivery extension implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, your delivery extension can be used with the Report Manager Subscription page.</span></span> <span data-ttu-id="d0c67-150">若要讓訂閱使用者介面可供使用，需要將延伸模組部署到報表管理員。</span><span class="sxs-lookup"><span data-stu-id="d0c67-150">To make the subscription user interface available, you need to deploy your extension to Report Manager.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a><span data-ttu-id="d0c67-151">將傳遞延伸模組組件部署到報表管理員</span><span class="sxs-lookup"><span data-stu-id="d0c67-151">To deploy a deliver extension assembly to Report Manager</span></span>  
  
1.  <span data-ttu-id="d0c67-152">將組件從您的執行位置複製到報表管理員的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="d0c67-152">Copy your assembly from your staging location to the bin directory of Report Manager.</span></span> <span data-ttu-id="d0c67-153">報表管理員 bin 目錄的預設位置是%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\reportmanager\bin。</span><span class="sxs-lookup"><span data-stu-id="d0c67-153">The default location of the Report Manager bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager\bin.</span></span>  
  
2.  <span data-ttu-id="d0c67-154">在複製組件檔之後，開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="d0c67-154">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="d0c67-155">RSReportServer.config 檔案位於%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\ReportServer 目錄。</span><span class="sxs-lookup"><span data-stu-id="d0c67-155">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="d0c67-156">您需要在傳遞延伸模組組件檔的組態檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="d0c67-156">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="d0c67-157">您可以使用 Visual Studio .NET 或簡單的文字編輯器 (如 [記事本]) 開啟組態檔。</span><span class="sxs-lookup"><span data-stu-id="d0c67-157">You can open the configuration file with Visual Studio .NET or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="d0c67-158">在 RSReportServer.config 檔中，找出 `DeliveryUI` 元素。</span><span class="sxs-lookup"><span data-stu-id="d0c67-158">Locate the `DeliveryUI` element in the RSReportServer.config file.</span></span> <span data-ttu-id="d0c67-159">應該針對您新建立的傳遞延伸模組，在下列位置建立項目：</span><span class="sxs-lookup"><span data-stu-id="d0c67-159">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="d0c67-160">針對您的傳遞延伸模組加入項目。</span><span class="sxs-lookup"><span data-stu-id="d0c67-160">Add an entry for your delivery extension.</span></span> <span data-ttu-id="d0c67-161">您的項目應該包含具有 `Extension` 和 `Name` 值的 `Type` 元素，且看起來可能與下列項目類似：</span><span class="sxs-lookup"><span data-stu-id="d0c67-161">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="d0c67-162">`Name` 的值是傳遞延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c67-162">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="d0c67-163">`Type` 的值是以逗號分隔的清單，包括實作 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 介面之類別的完整命名空間項目，後面接著組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="d0c67-163">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, followed by the name of your assembly (not including the .dll file extension).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d0c67-164">報表伺服器與報表管理員組態檔項目的 `Name` 屬性值必須相同。</span><span class="sxs-lookup"><span data-stu-id="d0c67-164">The value of the `Name` attribute must be identical for both the Report Server and Report Manager configuration file entries.</span></span> <span data-ttu-id="d0c67-165">如果它們不同，您的伺服器組態將無效。</span><span class="sxs-lookup"><span data-stu-id="d0c67-165">If they are not identical, your server configuration is not valid.</span></span>  
  
     <span data-ttu-id="d0c67-166">最後，針對為傳遞延伸模組授與 `FullTrust` 權限的自訂組件，加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="d0c67-166">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="d0c67-167">若要這麼做，您可以將程式碼群組加入至預設位於 C:\Program Files\Microsoft SQL Server \ MSRS10_50 中的 RSmgrpolicy.config 檔案。 \<InstanceName>\Reporting Services\reportmanager。</span><span class="sxs-lookup"><span data-stu-id="d0c67-167">You do this by adding the code group to the RSmgrpolicy.config file located by default in C:\Program Files\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager.</span></span> <span data-ttu-id="d0c67-168">您的程式碼群組可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c67-168">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="d0c67-169">URL 成員資格僅是您可以針對傳遞延伸模組所選擇的許多成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="d0c67-169">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="d0c67-170">如需中代碼啟用安全性的詳細資訊 [!INCLUDE[ssRS](../../../includes/ssrs.md)] ，請參閱[安全開發 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="d0c67-170">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="d0c67-171">確認部署</span><span class="sxs-lookup"><span data-stu-id="d0c67-171">Verifying the Deployment</span></span>  
 <span data-ttu-id="d0c67-172">您可以使用 Web 服務 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 方法來確認傳遞延伸模組是否已成功部署到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0c67-172">You can verify whether your delivery extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="d0c67-173">您也可以開啟報表管理員，然後確認延伸模組是否包含在訂閱的可用傳遞延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="d0c67-173">You can also open Report Manager and verify that your extension is included in the list of available delivery extensions for a subscription.</span></span> <span data-ttu-id="d0c67-174">如需報表管理員和訂閱的詳細資訊，請參閱[Reporting Services&#41;的訂閱和傳遞 &#40;](../../subscriptions/subscriptions-and-delivery-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d0c67-174">For more information about Report Manager and subscriptions, see [Subscriptions and Delivery &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c67-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0c67-175">See Also</span></span>  
 <span data-ttu-id="d0c67-176">[執行傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="d0c67-176">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="d0c67-177">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="d0c67-177">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
