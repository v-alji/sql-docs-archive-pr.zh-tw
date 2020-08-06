---
title: 如何：將資料處理延伸模組部署到報表伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708974"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a><span data-ttu-id="4f451-102">如何：將資料處理延伸模組部署到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="4f451-102">How to: Deploy a Data Processing Extension to a Report Server</span></span>
  <span data-ttu-id="4f451-103">報表伺服器使用資料處理延伸模組來擷取和處理轉譯報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="4f451-103">Report servers use data processing extensions for retrieving and processing data in rendered reports.</span></span> <span data-ttu-id="4f451-104">您應該將資料處理延伸模組組件部署到報表伺服器做為私人組件，</span><span class="sxs-lookup"><span data-stu-id="4f451-104">You should deploy your data processing extension assembly to a report server as a private assembly.</span></span> <span data-ttu-id="4f451-105">也需要在報表伺服器組態檔 RSReportServer.config 中建立項目。</span><span class="sxs-lookup"><span data-stu-id="4f451-105">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4f451-106">程序</span><span class="sxs-lookup"><span data-stu-id="4f451-106">Procedures</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="4f451-107">部署資料處理延伸模組組件</span><span class="sxs-lookup"><span data-stu-id="4f451-107">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="4f451-108">將組件從臨時位置複製到您要在其上使用資料處理延伸模組之報表伺服器的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="4f451-108">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the data processing extension.</span></span> <span data-ttu-id="4f451-109">報表伺服器 bin 目錄的預設位置是%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<*Instance Name*>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="4f451-109">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f451-110">這個步驟會避免升級到 SQL Server 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f451-110">This step will prevent an upgrade to a newer instance of SQL Server.</span></span> <span data-ttu-id="4f451-111">如需詳細資訊，請參閱＜ [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4f451-111">For more information, see [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
2.  <span data-ttu-id="4f451-112">在複製組件檔之後，開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4f451-112">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="4f451-113">RSReportServer.config 檔案位於 ReportServer 目錄中。</span><span class="sxs-lookup"><span data-stu-id="4f451-113">The RSReportServer.config file is located in the ReportServer directory.</span></span> <span data-ttu-id="4f451-114">您需要在資料處理延伸模組組件檔案的組態檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="4f451-114">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="4f451-115">您可以使用 Visual Studio 或簡單的文字編輯器 (如 [記事本]) 開啟設定檔。</span><span class="sxs-lookup"><span data-stu-id="4f451-115">You can open the configuration file with Visual Studio or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="4f451-116">在 RSReportServer.config 檔中，找出 `Data` 元素。</span><span class="sxs-lookup"><span data-stu-id="4f451-116">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="4f451-117">應該針對您新建立的資料處理延伸模組，在下列位置建立項目：</span><span class="sxs-lookup"><span data-stu-id="4f451-117">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="4f451-118">針對您的資料處理延伸模組加入項目。</span><span class="sxs-lookup"><span data-stu-id="4f451-118">Add an entry for your data processing extension.</span></span> <span data-ttu-id="4f451-119">您的項目應該包含具有 `Extension` 和 `Name` 值的 `Type` 元素，且看起來可能與下列項目類似：</span><span class="sxs-lookup"><span data-stu-id="4f451-119">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     <span data-ttu-id="4f451-120">`Name` 的值是資料處理延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="4f451-120">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="4f451-121">`Type` 的值是以逗號分隔的清單，包括實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 介面之類別的完整命名空間項目，後面接著組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="4f451-121">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="4f451-122">依預設值，資料處理延伸模組是可見的。</span><span class="sxs-lookup"><span data-stu-id="4f451-122">By default, data processing extensions are visible.</span></span> <span data-ttu-id="4f451-123">若要在使用者介面中隱藏延伸模組 (例如報表管理員)，請將 `Visible` 屬性加入至 `Extension` 元素，並將其設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4f451-123">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="4f451-124">針對為延伸模組授與 `FullTrust` 權限的自訂組件，加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="4f451-124">Add a code group for your custom assembly that grants `FullTrust` permission for your extension.</span></span> <span data-ttu-id="4f451-125">若要這麼做，您可以將程式碼群組新增至 rssrvpolicy.config 檔案，該檔案預設位於%ProgramFiles%\Microsoft SQL Server \\<MSRS10_50 中。 \<*Instance Name*>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="4f451-125">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="4f451-126">您的程式碼群組可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f451-126">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="4f451-127">URL 成員資格僅是您可以針對資料處理延伸模組所選擇的許多成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="4f451-127">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="4f451-128">如需 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中程式碼存取安全性的詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4f451-128">For more information about code access security in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="4f451-129">確認部署</span><span class="sxs-lookup"><span data-stu-id="4f451-129">Verifying the Deployment</span></span>  
 <span data-ttu-id="4f451-130">您可以使用 Web 服務 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 方法來確認資料處理延伸模組是否已成功部署到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4f451-130">You can verify whether your data processing extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="4f451-131">您也可以開啟報表管理員，然後確認延伸模組是否包含在可用資料來源的清單。</span><span class="sxs-lookup"><span data-stu-id="4f451-131">You can also open Report Manager and verify that your extension is included in the list of available data sources.</span></span> <span data-ttu-id="4f451-132">如需報表管理員和資料來源的詳細資訊，請參閱[建立、修改及刪除共用資料來源 &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f451-132">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f451-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f451-133">See Also</span></span>  
 <span data-ttu-id="4f451-134">[部署資料處理延伸模組](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="4f451-134">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="4f451-135">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4f451-135">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="4f451-136">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="4f451-136">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="4f451-137">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="4f451-137">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
