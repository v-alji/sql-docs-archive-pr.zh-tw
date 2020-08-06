---
title: 註冊標準的 .NET Framework Data Provider (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fd26f9c7fa163d9e6005d42e24c7b1483987f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687494"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a><span data-ttu-id="72317-102">註冊標準的 .NET Framework Data Provider (SSRS)</span><span class="sxs-lookup"><span data-stu-id="72317-102">Register a Standard .NET Framework Data Provider (SSRS)</span></span>
  <span data-ttu-id="72317-103">若要使用協力廠商的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者來擷取 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表資料集的資料，您必須在兩個位置部署並註冊 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者組件：報表撰寫用戶端與報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="72317-103">To use a third-party [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to retrieve data for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report dataset, you need to deploy and register the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly in two locations: on the report authoring client and on the report server.</span></span> <span data-ttu-id="72317-104">在報表撰寫用戶端上，您必須註冊資料提供者做為資料來源類型，並將其與查詢設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="72317-104">On the report authoring client, you must register the data provider as a data source type and associate it with a query designer.</span></span> <span data-ttu-id="72317-105">然後您可以在建立報表資料集時，選取此資料提供者做為資料來源的類型。</span><span class="sxs-lookup"><span data-stu-id="72317-105">You can then select this data provider as a type of data source when you create a report dataset.</span></span> <span data-ttu-id="72317-106">相關聯的查詢設計工具便會開啟，協助您建立此資料來源類型的查詢。</span><span class="sxs-lookup"><span data-stu-id="72317-106">The associated query designer opens to help you create queries for this data source type.</span></span> <span data-ttu-id="72317-107">在報表伺服器上，您必須註冊資料提供者，做為資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="72317-107">On the report server, you must register the data provider as a data source type.</span></span> <span data-ttu-id="72317-108">然後您可以處理使用此資料提供者，從資料來源擷取資料的已發行報表。</span><span class="sxs-lookup"><span data-stu-id="72317-108">You can then process published reports that retrieve data from a data source using this data provider.</span></span>  
  
 <span data-ttu-id="72317-109">協力廠商的資料提供者不一定會提供適用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料處理延伸模組的所有功能。</span><span class="sxs-lookup"><span data-stu-id="72317-109">Third-party data providers do not necessarily provide all the functionality available with the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="72317-110">如需詳細資訊，請參閱 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="72317-110">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span> <span data-ttu-id="72317-111">若要了解有關擴充 .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72317-111">To learn about extending the functionality of a .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span></span> <span data-ttu-id="72317-112"> 資料提供者，請參閱[實作資料處理延伸模組](../extensions/data-processing/implementing-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="72317-112">data provider, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="72317-113">您需要管理員認證才能安裝與註冊資料提供者。</span><span class="sxs-lookup"><span data-stu-id="72317-113">You need administrator credentials to install and register data providers.</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a><span data-ttu-id="72317-114">在報表伺服器上註冊 .NET Framework Data Provider</span><span class="sxs-lookup"><span data-stu-id="72317-114">Registering a .NET Framework Data Provider on the Report Server</span></span>  
 <span data-ttu-id="72317-115">若要在報表伺服器上，處理使用此 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的已發行報表，您必須在報表伺服器上安裝組件。</span><span class="sxs-lookup"><span data-stu-id="72317-115">In order to process published reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider on the report server, you need to install the assembly on the report server.</span></span> <span data-ttu-id="72317-116">您必須修改兩個組態檔。</span><span class="sxs-lookup"><span data-stu-id="72317-116">You must modify two configuration files.</span></span> <span data-ttu-id="72317-117">修改 rsreportserver.config 以註冊資料提供者。</span><span class="sxs-lookup"><span data-stu-id="72317-117">Modify rsreportserver.config to register the data provider.</span></span> <span data-ttu-id="72317-118">修改 rssrvpolicy.config 以授與組件的程式碼存取安全性權限。</span><span class="sxs-lookup"><span data-stu-id="72317-118">Modify rssrvpolicy.config to grant code access security permissions for the assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a><span data-ttu-id="72317-119">在報表伺服器上安裝資料提供者組件</span><span class="sxs-lookup"><span data-stu-id="72317-119">To install a data provider assembly on the report server</span></span>  
  
1.  <span data-ttu-id="72317-120">在您要使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的報表伺服器上，巡覽至 bin 目錄的預設位置。</span><span class="sxs-lookup"><span data-stu-id="72317-120">Navigate to the default location of the bin directory on the report server on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="72317-121">報表伺服器 bin 目錄的預設位置是 *\<drive>* ： \Program Files\Microsoft SQL Server \ MSRS10_50. MSSQLSERVER\Reporting services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="72317-121">The default location of the report server bin directory is *\<drive>*:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span>  
  
2.  <span data-ttu-id="72317-122">將組件從您的臨時位置複製到報表伺服器的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="72317-122">Copy your assembly from your staging location to the bin directory of the report server.</span></span> <span data-ttu-id="72317-123">或者，您可以將組件載入至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="72317-123">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="72317-124">如需詳細資訊，請參閱 MSDN [SDK 文件集中的＜](https://go.microsoft.com/fwlink/?linkid=63912) 使用組件和全域組件快取 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ＞。</span><span class="sxs-lookup"><span data-stu-id="72317-124">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a><span data-ttu-id="72317-125">在報表伺服器上註冊 .NET 資料提供者</span><span class="sxs-lookup"><span data-stu-id="72317-125">To register a .NET data provider on the report server</span></span>  
  
1.  <span data-ttu-id="72317-126">在 bin 的 ReportServer 上層目錄中，製作 RSReportServer.config 檔的備份。</span><span class="sxs-lookup"><span data-stu-id="72317-126">Make a backup of the RSReportServer.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="72317-127">開啟 RSReportServer.config。您可以利用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器 (如 [記事本]) 開啟組態檔。</span><span class="sxs-lookup"><span data-stu-id="72317-127">Open RSReportServer.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="72317-128">在 RSReportServer.config 檔中，找出 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="72317-128">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="72317-129">在下列位置應該就會建立一個 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的項目：</span><span class="sxs-lookup"><span data-stu-id="72317-129">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="72317-130">加入 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的項目。</span><span class="sxs-lookup"><span data-stu-id="72317-130">Add an entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
    |<span data-ttu-id="72317-131">屬性</span><span class="sxs-lookup"><span data-stu-id="72317-131">Attribute</span></span>|<span data-ttu-id="72317-132">描述</span><span class="sxs-lookup"><span data-stu-id="72317-132">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="72317-133">為資料提供者提供唯一的名稱，例如， **MyNETDataProvider**。</span><span class="sxs-lookup"><span data-stu-id="72317-133">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="72317-134">`Name` 屬性的最大長度為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="72317-134">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="72317-135">該名稱在組態檔之 `Extension` 元素的所有元素中，必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="72317-135">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="72317-136">當您建立新的資料來源時，您在此處包含的值會出現在資料來源類型的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="72317-136">The value you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="72317-137">輸入一個逗號分隔清單，其中包含實作 <xref:System.Data.IDbConnection> 介面之類別的完整命名空間，後面緊接著 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="72317-137">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="72317-138">例如，若是部署至報表伺服器 bin 目錄的 DLL，該項目可能類似如下：</span><span class="sxs-lookup"><span data-stu-id="72317-138">For example, the entry might resemble the following for a DLL deployed to the report server bin directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="72317-139">如果您將組件載入至全域組件快取 (GAC)，您必須提供強式名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="72317-139">If you load your assembly into the global assembly cache (GAC), you must provide the strong name properties.</span></span> <span data-ttu-id="72317-140">例如：</span><span class="sxs-lookup"><span data-stu-id="72317-140">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a><span data-ttu-id="72317-141">為 .NET 資料提供者設定程式碼群組原則</span><span class="sxs-lookup"><span data-stu-id="72317-141">To set the code group policy for a .NET data provider</span></span>  
  
1.  <span data-ttu-id="72317-142">在 bin 的 ReportServer 上層目錄中，製作 rssrvpolicy.config 檔的備份副本。</span><span class="sxs-lookup"><span data-stu-id="72317-142">Make a backup copy of the rssrvpolicy.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="72317-143">開啟 rssrvpolicy.config。您可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器（如 [記事本]）開啟設定檔。</span><span class="sxs-lookup"><span data-stu-id="72317-143">Open rssrvpolicy.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="72317-144">在 rssrvpolicy.config 檔中，找出 `CodeGroup` 元素。</span><span class="sxs-lookup"><span data-stu-id="72317-144">Locate the `CodeGroup` element in the rssrvpolicy.config file.</span></span>  
  
4.  <span data-ttu-id="72317-145">針對授與 `FullTrust` 權限的資料提供者組件，加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="72317-145">Add a code group for the data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="72317-146">您的程式碼群組可能類似如下：</span><span class="sxs-lookup"><span data-stu-id="72317-146">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="72317-147">URL 成員資格僅是您可以針對資料提供者選取的多個成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="72317-147">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration"></a><span data-ttu-id="72317-148">確認部署與註冊</span><span class="sxs-lookup"><span data-stu-id="72317-148">Verifying the Deployment and Registration</span></span>  
 <span data-ttu-id="72317-149">您可以確認是否將資料提供者成功部署至報表伺服器，方法是，開啟報表管理員，然後確認該資料提供者包含在可用資料來源的清單中。</span><span class="sxs-lookup"><span data-stu-id="72317-149">You can verify whether the data provider was deployed successfully to the report server by opening Report Manager and verifying that the data provider is included in the list of available data sources.</span></span> <span data-ttu-id="72317-150">如需報表管理員和資料來源的詳細資訊，請參閱[建立、修改及刪除共用資料來源 &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="72317-150">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a><span data-ttu-id="72317-151">在報表設計師用戶端上註冊 .NET Framework Data Provider</span><span class="sxs-lookup"><span data-stu-id="72317-151">Registering a .NET Framework Data Provider on the Report Designer Client</span></span>  
 <span data-ttu-id="72317-152">若要針對資料來源撰寫使用此 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的報表，您必須在執行報表設計師的用戶端電腦上安裝該組件。</span><span class="sxs-lookup"><span data-stu-id="72317-152">In order to author reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider for a data source, you must install the assembly on your client computer that runs Report Designer.</span></span> <span data-ttu-id="72317-153">您必須修改兩個組態檔。</span><span class="sxs-lookup"><span data-stu-id="72317-153">You must modify two configuration files.</span></span> <span data-ttu-id="72317-154">修改 RSReportDesigner.config 以註冊資料提供者做為資料來源，以及使用一般查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="72317-154">Modify RSReportDesigner.config to register the data provider as a data source and to use the generic query designer.</span></span> <span data-ttu-id="72317-155">修改 RSPreviewPolicy.config 以授與資料提供者組件的程式碼存取安全性權限。</span><span class="sxs-lookup"><span data-stu-id="72317-155">Modify RSPreviewPolicy.config to grant code access security permissions for the data provider assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a><span data-ttu-id="72317-156">在報表設計師用戶端上安裝資料提供者組件</span><span class="sxs-lookup"><span data-stu-id="72317-156">To install a data provider assembly on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="72317-157">在您要使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的報表設計師用戶端上，巡覽至 PrivateAssemblies 目錄的預設位置。</span><span class="sxs-lookup"><span data-stu-id="72317-157">Navigate to the default location of the PrivateAssemblies directory on the Report Designer client on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="72317-158">PrivateAssemblies 目錄的預設位置是 *\<drive>* ： \Program Files\Microsoft Visual Studio 9.0 \ common7\ide\privateassemblies。</span><span class="sxs-lookup"><span data-stu-id="72317-158">The default location of the PrivateAssemblies directory is *\<drive>*:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="72317-159">將組件從您的臨時位置複製到報表設計師用戶端的 PrivateAssemblies 目錄。</span><span class="sxs-lookup"><span data-stu-id="72317-159">Copy your assembly from your staging location to the PrivateAssemblies directory of the Report Designer client.</span></span> <span data-ttu-id="72317-160">或者，您可以將組件載入至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="72317-160">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="72317-161">如需詳細資訊，請參閱 MSDN [SDK 文件集中的＜](https://go.microsoft.com/fwlink/?linkid=63912) 使用組件和全域組件快取 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ＞。</span><span class="sxs-lookup"><span data-stu-id="72317-161">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="72317-162">在報表設計師用戶端上註冊 .NET 資料提供者</span><span class="sxs-lookup"><span data-stu-id="72317-162">To register a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="72317-163">在 PrivateAssemblies 目錄中，製作 RSReportDesigner.config 檔的備份副本。</span><span class="sxs-lookup"><span data-stu-id="72317-163">Make a backup copy of the RSReportDesigner.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="72317-164">利用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器 (如 [記事本]) 開啟 RSReportDesigner.config。</span><span class="sxs-lookup"><span data-stu-id="72317-164">Open RSReportDesigner.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="72317-165">在 RSReportDesigner.config 檔中，找出 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="72317-165">Locate the `Data` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="72317-166">在下列位置應該就會建立一個資料提供者的項目：</span><span class="sxs-lookup"><span data-stu-id="72317-166">An entry for the data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="72317-167">加入資料提供者的項目。</span><span class="sxs-lookup"><span data-stu-id="72317-167">Add an entry for the data provider.</span></span>  
  
    |<span data-ttu-id="72317-168">屬性</span><span class="sxs-lookup"><span data-stu-id="72317-168">Attribute</span></span>|<span data-ttu-id="72317-169">描述</span><span class="sxs-lookup"><span data-stu-id="72317-169">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="72317-170">為資料提供者提供唯一的名稱，例如， **MyNETDataProvider**。</span><span class="sxs-lookup"><span data-stu-id="72317-170">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="72317-171">`Name` 屬性的最大長度為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="72317-171">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="72317-172">該名稱在組態檔之 `Extension` 元素的所有元素中，必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="72317-172">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="72317-173">當您建立新的資料來源時，您在此處包含的值會出現在資料來源類型的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="72317-173">The value that you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="72317-174">輸入一個逗號分隔清單，其中包含實作 <xref:System.Data.IDbConnection> 介面之類別的完整命名空間，後面緊接著 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="72317-174">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="72317-175">例如，若是部署至 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies 目錄的 DLL，該項目可能類似如下：</span><span class="sxs-lookup"><span data-stu-id="72317-175">For example, the entry might resemble the following for a DLL deployed to the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="72317-176">如果您將組件載入至 GAC，您必須提供強式名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="72317-176">If you load your assembly into the GAC, you must provide the strong name properties.</span></span> <span data-ttu-id="72317-177">例如：</span><span class="sxs-lookup"><span data-stu-id="72317-177">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  <span data-ttu-id="72317-178">在 RSReportDesigner.config 檔中，找出 `Designer` 元素。</span><span class="sxs-lookup"><span data-stu-id="72317-178">Locate the `Designer` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="72317-179">在下列位置應該就會建立一個 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者的項目：</span><span class="sxs-lookup"><span data-stu-id="72317-179">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  <span data-ttu-id="72317-180">將下列項目加入至 RSReportDesigner.config 檔的 `Designer` 元素下。</span><span class="sxs-lookup"><span data-stu-id="72317-180">Add the following entry to the RSReportDesigner.config file under the `Designer` element.</span></span> <span data-ttu-id="72317-181">您僅需要以您在之前項目中提供的名稱，取代 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="72317-181">You need to replace only the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="72317-182">在報表設計師用戶端上設定 .NET 資料提供者的程式碼群組原則</span><span class="sxs-lookup"><span data-stu-id="72317-182">To set the code group policy for a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="72317-183">在 PrivateAssemblies 目錄中，製作 RSPreviewPolicy.config 檔的備份副本。</span><span class="sxs-lookup"><span data-stu-id="72317-183">Make a backup copy of the RSPreviewPolicy.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="72317-184">利用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器 (如「記事本」) 開啟 RSPreviewPolicy.config。</span><span class="sxs-lookup"><span data-stu-id="72317-184">Open RSPreviewPolicy.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="72317-185">在 RSPreviewPolicy.config 檔中，找出 `CodeGroup` 元素。</span><span class="sxs-lookup"><span data-stu-id="72317-185">Locate the `CodeGroup` element in the RSPreviewPolicy.config file.</span></span>  
  
4.  <span data-ttu-id="72317-186">針對授與 `FullTrust` 權限的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者組件，加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="72317-186">Add a code group for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="72317-187">您的程式碼群組可能類似如下：</span><span class="sxs-lookup"><span data-stu-id="72317-187">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="72317-188">URL 成員資格僅是您可以針對資料提供者選取的多個成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="72317-188">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a><span data-ttu-id="72317-189">在報表設計師用戶端上確認部署與註冊</span><span class="sxs-lookup"><span data-stu-id="72317-189">Verifying the Deployment and Registration on the Report Designer Client</span></span>  
 <span data-ttu-id="72317-190">在您可以確認部署之前，必須在本機電腦上，關閉 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="72317-190">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="72317-191">在您已經結束所有目前的工作階段後，您可以確認是否已將您的資料提供者成功部署至報表設計師，方法是，在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中建立新的報表專案。</span><span class="sxs-lookup"><span data-stu-id="72317-191">After you have ended all current sessions, you can verify whether your data provider was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="72317-192">當您從報表建立新的資料集時，資料提供者應該會包含在可用資料來源類型的清單中。</span><span class="sxs-lookup"><span data-stu-id="72317-192">The data provider should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="platform-considerations"></a><span data-ttu-id="72317-193">平台考量</span><span class="sxs-lookup"><span data-stu-id="72317-193">Platform Considerations</span></span>  
 <span data-ttu-id="72317-194">在 64 位元 (x64) 平台上， [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 會以 32 位元 WOW 模式執行。</span><span class="sxs-lookup"><span data-stu-id="72317-194">On a 64-bit (x64) platform, [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] runs in 32-bit WOW mode.</span></span> <span data-ttu-id="72317-195">當您在 x64 平台上撰寫報表時，您需要將 32 位元資料提供者安裝在報表撰寫用戶端上，才能預覽您的報表。</span><span class="sxs-lookup"><span data-stu-id="72317-195">When you author reports on an x64 platform, you need 32-bit data providers installed on the report authoring client in order to preview your reports.</span></span> <span data-ttu-id="72317-196">如果您在相同的系統上發行報表，您需要 x64 資料提供者，才能使用報表管理員檢視報表。</span><span class="sxs-lookup"><span data-stu-id="72317-196">If you publish the report on the same system, you need x64 data providers to view the report with Report Manager.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="72317-197">不支援以 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]為基礎的平台。</span><span class="sxs-lookup"><span data-stu-id="72317-197">is not supported for [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based platforms.</span></span>  
  
 <span data-ttu-id="72317-198">與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 一起安裝的資料處理延伸模組原始就必須針對每個平台編譯，而且必須安裝在正確的位置。</span><span class="sxs-lookup"><span data-stu-id="72317-198">The data processing extensions that are installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] must be compiled natively for each platform and installed in the correct locations.</span></span> <span data-ttu-id="72317-199">如果您要註冊自訂的資料提供者或標準的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者，則原始就需要針對適當的平台編譯，而且需要安裝在適當的位置。</span><span class="sxs-lookup"><span data-stu-id="72317-199">If you register a custom data provider or a standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider, it needs to be compiled natively for the appropriate platform and installed the appropriate locations.</span></span> <span data-ttu-id="72317-200">如果您是在 32 位元平台上執行，資料提供者必須針對 32 位元平台編譯。</span><span class="sxs-lookup"><span data-stu-id="72317-200">If you are running on a 32-bit platform, the data provider must be compiled for a 32-bit platform.</span></span> <span data-ttu-id="72317-201">如果您是在 64 位元平台上執行，資料提供者則必須針對 64 位元平台編譯。</span><span class="sxs-lookup"><span data-stu-id="72317-201">If you are running on a 64-bit platform, the data provider must be compiled for the 64-bit platform.</span></span> <span data-ttu-id="72317-202">您無法在 64 位元平台上，使用以 64 位元介面包裝的 32 位元資料提供者。</span><span class="sxs-lookup"><span data-stu-id="72317-202">You cannot use a 32-bit data provider wrapped with 64-bit interfaces on a 64 bit platform.</span></span> <span data-ttu-id="72317-203">如需有關資料提供者是否可以在已安裝的平台上運作的詳細資訊，請查閱您的協力廠商軟體。</span><span class="sxs-lookup"><span data-stu-id="72317-203">Check your third-party software for information about whether the data provider will work on the installed platform.</span></span> <span data-ttu-id="72317-204">如需資料提供者與平台支援的詳細資訊，請參閱 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="72317-204">For more information about data providers and platform support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72317-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72317-205">See Also</span></span>  
 <span data-ttu-id="72317-206">[設定和管理報表伺服器 &#40;SSRS 原生模式&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="72317-206">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="72317-207">[執行資料處理延伸模組](../extensions/data-processing/implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="72317-207">[Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="72317-208">[Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="72317-208">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="72317-209">Reporting Services 中的程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="72317-209">Code Access Security in Reporting Services</span></span>](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
