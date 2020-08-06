---
title: 存取 Reporting Services WMI 提供者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db0848ae8c988229a1804bbd4b19e6c38b68c35f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706194"
---
# <a name="access-the-reporting-services-wmi-provider"></a><span data-ttu-id="ac853-102">存取 Reporting Services WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="ac853-102">Access the Reporting Services WMI Provider</span></span>
  <span data-ttu-id="ac853-103">Reporting Services WMI 提供者會公開兩個 WMI 類別，可透過指令碼管理原生模式報表伺服器執行個體：</span><span class="sxs-lookup"><span data-stu-id="ac853-103">The Reporting Services WMI provider exposes two WMI classes for administration of Native mode report server instances through scripting:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac853-104">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 版開始，只有原生模式報表伺服器才支援 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="ac853-104">Starting with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, the WMI provider is supported for only native mode report servers.</span></span> <span data-ttu-id="ac853-105">SharePoint 模式報表伺服器可以透過 SharePoint 管理中心頁面和 PowerShell 指令碼管理。</span><span class="sxs-lookup"><span data-stu-id="ac853-105">SharePoint mode report servers can be managed with SharePoint Central Administration pages and PowerShell scripts.</span></span>  
  
|<span data-ttu-id="ac853-106">類別</span><span class="sxs-lookup"><span data-stu-id="ac853-106">Class</span></span>|<span data-ttu-id="ac853-107">命名空間</span><span class="sxs-lookup"><span data-stu-id="ac853-107">Namespace</span></span>|<span data-ttu-id="ac853-108">描述</span><span class="sxs-lookup"><span data-stu-id="ac853-108">Description</span></span>|  
|-----------|---------------|-----------------|  
|<span data-ttu-id="ac853-109">MSReportServer_Instance</span><span class="sxs-lookup"><span data-stu-id="ac853-109">MSReportServer_Instance</span></span>|<span data-ttu-id="ac853-110">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11</span><span class="sxs-lookup"><span data-stu-id="ac853-110">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11</span></span>|<span data-ttu-id="ac853-111">提供用戶端連接至已安裝之報表伺服器所需的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="ac853-111">Provides basic information required for a client to connect to an installed report server.</span></span>|  
|<span data-ttu-id="ac853-112">MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="ac853-112">MSReportServer_ConfigurationSetting</span></span>|<span data-ttu-id="ac853-113">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11\Admin</span><span class="sxs-lookup"><span data-stu-id="ac853-113">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11\Admin</span></span>|<span data-ttu-id="ac853-114">代表報表伺服器執行個體的安裝與執行階段參數。</span><span class="sxs-lookup"><span data-stu-id="ac853-114">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="ac853-115">這些參數是儲存在報表伺服器的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="ac853-115">These parameters are stored in the configuration file for the report server.</span></span><br /><br /> <span data-ttu-id="ac853-116">**\*\* 重要事項 \*\*** 這個類別只能透過管理權限存取。</span><span class="sxs-lookup"><span data-stu-id="ac853-116">**\*\* Important \*\*** This class is only accessible with administrative privileges.</span></span>|  
  
 <span data-ttu-id="ac853-117">針對每一個報表伺服器執行個體會建立上述每一個類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac853-117">An instance of each of the above classes is created for each report server instance.</span></span> <span data-ttu-id="ac853-118">您可以使用任何 Microsoft 或協力廠商工具來存取報表伺服器公開的 WMI 物件，包括 .NET Framework 本身公開的 WMI 程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="ac853-118">You can use any Microsoft or third party tools to access the WMI objects exposed by the report server, including WMI programming interfaces exposed by the .NET Framework itself.</span></span> <span data-ttu-id="ac853-119">本主題描述如何存取及使用 WMI 類別執行個體搭配 PowerShell 命令 [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ac853-119">This topic describes how to access and use the WMI class instances with the PowerShell command [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).</span></span>  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a><span data-ttu-id="ac853-120">判斷命名空間字串中的執行個體名稱</span><span class="sxs-lookup"><span data-stu-id="ac853-120">Determine the Instance Name in the Namespace String</span></span>  
 <span data-ttu-id="ac853-121">命名空間路徑中 Reporting Services WMI 類別的執行個體名稱，是您安裝具名 Reporting Services 執行個體時指定的執行個體名稱編碼。</span><span class="sxs-lookup"><span data-stu-id="ac853-121">The instance name in the namespace path for the Reporting Services WMI classes is an encoding of the instance names that you specify when installing the named Reporting Services instances.</span></span> <span data-ttu-id="ac853-122">也就是說，執行個體名稱中的特殊字元會經過編碼。</span><span class="sxs-lookup"><span data-stu-id="ac853-122">Namely, special characters in the instance names are encoded.</span></span> <span data-ttu-id="ac853-123">例如，底線 (_) 會編碼為 "_5f"，因此 "My_Instance" 這個執行個體名稱在 WMI 命名空間路徑中就會編碼為 "My_5fInstance"。</span><span class="sxs-lookup"><span data-stu-id="ac853-123">For example, an underline (_) is encoded as "_5f", so an instance name of "My_Instance" is encoded as "My_5fInstance" in the WMI namespace path.</span></span>  
  
 <span data-ttu-id="ac853-124">若要列出 WMI 命名空間路徑中報表伺服器執行個體的編碼執行個體名稱，請使用下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="ac853-124">To list the encoded instance names of your report server instances in the WMI namespace path, use the following PowerShell command:</span></span>  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a><span data-ttu-id="ac853-125">使用 PowerShell 存取 WMI 類別</span><span class="sxs-lookup"><span data-stu-id="ac853-125">Access the WMI Classes Using PowerShell</span></span>  
 <span data-ttu-id="ac853-126">若要存取 WMI 類別，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ac853-126">To access the WMI classes, run the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 <span data-ttu-id="ac853-127">例如，若要存取主機 myrshost 的預設報表伺服器執行個體上的 MSReportServer_ConfigurationSetting 類別，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ac853-127">For example, to access the MSReportServer_ConfigurationSetting class on the default report server instance of the host myrshost, run the following command.</span></span> <span data-ttu-id="ac853-128">預設報表伺服器執行個體必須安裝在 myrshost 上，這個命令才會成功。</span><span class="sxs-lookup"><span data-stu-id="ac853-128">The default report server instance must be installed on myrshost for this command to succeed.</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 <span data-ttu-id="ac853-129">這個命令語法會輸出所有類別屬性名稱和值。</span><span class="sxs-lookup"><span data-stu-id="ac853-129">This command syntax outputs all class property names and values.</span></span> <span data-ttu-id="ac853-130">請注意，即使您是存取預設報表伺服器執行個體 (RS_MSSQLSERVER) 的命名空間中的類別，仍會傳回 MSReportServer_ConfigurationSetting 類別的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac853-130">Note that all instances of the class MSReportServer_ConfigurationSetting is returned, even though you are accessing the class in the namespace of the default report server instance (RS_MSSQLSERVER).</span></span> <span data-ttu-id="ac853-131">例如，如果 myrshost 上安裝了預設報表伺服器執行個體和名為 SHAREPOINT 的具名報表伺服器執行個體，則這個命令將傳回兩個 WMI 物件，並輸出這兩個報表伺服器執行個體的屬性名稱和值。</span><span class="sxs-lookup"><span data-stu-id="ac853-131">For example, if myrshost is installed with the default report server instance and a named report server instance called SHAREPOINT, this command will return two WMI objects and output the property names and values for both report server instances.</span></span>  
  
 <span data-ttu-id="ac853-132">若要在傳回多個執行個體時傳回特定類別的執行個體，請使用 -Filter 參數，依據擁有唯一值的屬性 (例如 InstanceName) 篩選結果。</span><span class="sxs-lookup"><span data-stu-id="ac853-132">To return a specific class instance when multiple instances are returned, use the -Filter parameter to filter the results based on properties with unique values such as InstanceName.</span></span> <span data-ttu-id="ac853-133">例如，若只要傳回預設報表伺服器執行個體的 WMI 物件，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="ac853-133">For example, to return only the WMI object for the default report server instance, use the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a><span data-ttu-id="ac853-134">查詢可用的方法和屬性</span><span class="sxs-lookup"><span data-stu-id="ac853-134">Query the Available Methods and Properties</span></span>  
 <span data-ttu-id="ac853-135">若要查看其中一個 Reporting Services WMI 類別中可用的方法和屬性，請將結果從 Get-WmiObject 管道傳送到 Get-Member 命令。</span><span class="sxs-lookup"><span data-stu-id="ac853-135">To see what methods and properties are available in one of the Reporting Services WMI classes, pipe the results from Get-WmiObject to the Get-Member command.</span></span> <span data-ttu-id="ac853-136">例如：</span><span class="sxs-lookup"><span data-stu-id="ac853-136">For example:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 <span data-ttu-id="ac853-137">如需 Reporting Services WMI 類別之屬性和方法的相關檔，請參閱 ...。</span><span class="sxs-lookup"><span data-stu-id="ac853-137">For documentation on the properties and methods of the Reporting Services WMI classes, see ....</span></span>  
  
## <a name="use-a-wmi-method-or-property"></a><span data-ttu-id="ac853-138">使用 WMI 方法或屬性</span><span class="sxs-lookup"><span data-stu-id="ac853-138">Use a WMI Method or Property</span></span>  
 <span data-ttu-id="ac853-139">您具有 Reporting Services 類別的 WMI 物件並且知道可用的方法和屬性之後，就可以使用這些方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="ac853-139">Once you have the WMI objects to the Reporting Services classes and know the available methods and properties, you can use these methods and properties.</span></span> <span data-ttu-id="ac853-140">例如，如果您擁有名為 SHAREPOINT 的 SharePoint 整合模式具名報表伺服器執行個體，請使用下列命令序列擷取 SharePoint 管理中心網站的 URL：</span><span class="sxs-lookup"><span data-stu-id="ac853-140">For example, if you have a named report server instance in SharePoint integrated mode called SHAREPOINT, use the following command sequence to retrieve the URL for the SharePoint Central Administration site:</span></span>  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac853-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac853-141">See Also</span></span>
 <span data-ttu-id="ac853-142">[Reporting Services WMI 提供者程式庫參考 &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ac853-142">[Reporting Services WMI Provider Library Reference &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="ac853-143">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="ac853-143">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
