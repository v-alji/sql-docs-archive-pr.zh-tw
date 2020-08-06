---
title: Web 組態參考 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 71e72bdb45a29c29c2187c381f67a525f0bd51c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707638"
---
# <a name="web-configuration-reference-master-data-services"></a><span data-ttu-id="59de9-102">Web 組態參考 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="59de9-102">Web Configuration Reference (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="59de9-103">在 Web.config 檔案中包含讓 Internet Information Services (IIS) 主控 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式和 Web 服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="59de9-103">uses a Web.config file to contain the configuration settings that enable Internet Information Services (IIS) to host the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and the Web service.</span></span> <span data-ttu-id="59de9-104">這個 Web.config 檔案位於 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 安裝路徑的 WebApplication 資料夾。</span><span class="sxs-lookup"><span data-stu-id="59de9-104">This Web.config file is located in the WebApplication folder of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] installation path.</span></span> <span data-ttu-id="59de9-105">如需路徑和權限的詳細資訊，請參閱[資料夾和檔案的權限 &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="59de9-105">For more information about the path and permissions, see [Folder and File Permissions &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md).</span></span>  
  
## <a name="webconfig-elements"></a><span data-ttu-id="59de9-106">Web.Config 元素</span><span class="sxs-lookup"><span data-stu-id="59de9-106">Web.Config Elements</span></span>  
 <span data-ttu-id="59de9-107">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **\<masterDataServices>** 除了標準的 IIS、.NET Framework、ASP.NET 和 WINDOWS COMMUNICATION FOUNDATION (WCF) configuration 元素之外，Web.config 檔案還包含自訂元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-107">The Web.config file contains a custom [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] element, **\<masterDataServices>**, in addition to standard IIS, .NET Framework, ASP.NET, and Windows Communication Foundation (WCF) configuration elements.</span></span> <span data-ttu-id="59de9-108">下表描述 Web.config 檔案中包含的元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-108">The following table describes the elements included in the Web.config file.</span></span>  
  
|<span data-ttu-id="59de9-109">組態元素</span><span class="sxs-lookup"><span data-stu-id="59de9-109">Configuration Element</span></span>|<span data-ttu-id="59de9-110">描述</span><span class="sxs-lookup"><span data-stu-id="59de9-110">Description</span></span>|  
|---------------------------|-----------------|  
|`masterDataServices`|<span data-ttu-id="59de9-111">自訂元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-111">Custom element.</span></span> <span data-ttu-id="59de9-112">將 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服務連接到 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="59de9-112">Connects the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web service to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>|  
|`connectionStrings`|<span data-ttu-id="59de9-113">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-113">ASP.NET element.</span></span> <span data-ttu-id="59de9-114">如需詳細資訊，請參閱 MSDN Library 中的 [connectionStrings 項目 (ASP.NET 設定結構描述)](https://go.microsoft.com/fwlink/?LinkId=178347) 。</span><span class="sxs-lookup"><span data-stu-id="59de9-114">For more information, see [connectionStrings Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178347) in the MSDN Library.</span></span>|  
|`system.web`|<span data-ttu-id="59de9-115">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-115">ASP.NET element.</span></span> <span data-ttu-id="59de9-116">如需詳細資訊，請參閱 MSDN Library 中的 [system.web 項目 (ASP.NET 設定結構描述)](https://go.microsoft.com/fwlink/?LinkId=178348) 。</span><span class="sxs-lookup"><span data-stu-id="59de9-116">For more information, see [system.web Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178348) in the MSDN Library.</span></span>|  
|`startup`|<span data-ttu-id="59de9-117">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-117">.NET Framework element.</span></span> <span data-ttu-id="59de9-118">如需詳細資訊，請參閱 MSDN Library 中的[ \<startup> 元素](https://go.microsoft.com/fwlink/?LinkId=178349)。</span><span class="sxs-lookup"><span data-stu-id="59de9-118">For more information, see [\<startup> Element](https://go.microsoft.com/fwlink/?LinkId=178349) in the MSDN Library.</span></span>|  
|`runtime`|<span data-ttu-id="59de9-119">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-119">.NET Framework element.</span></span> <span data-ttu-id="59de9-120">如需詳細資訊，請參閱 MSDN Library 中的[ \<runtime> 元素](https://go.microsoft.com/fwlink/?LinkId=178350)。</span><span class="sxs-lookup"><span data-stu-id="59de9-120">For more information, see [\<runtime> Element](https://go.microsoft.com/fwlink/?LinkId=178350) in the MSDN Library.</span></span>|  
|`system.codedom`|<span data-ttu-id="59de9-121">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-121">.NET Framework element.</span></span> <span data-ttu-id="59de9-122">如需詳細資訊，請參閱 MSDN Library 中的[ \<system.codedom> 元素](https://go.microsoft.com/fwlink/?LinkId=178351)。</span><span class="sxs-lookup"><span data-stu-id="59de9-122">For more information, see [\<system.codedom> Element](https://go.microsoft.com/fwlink/?LinkId=178351) in the MSDN Library.</span></span>|  
|`system.web.extensions`|<span data-ttu-id="59de9-123">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-123">ASP.NET element.</span></span> <span data-ttu-id="59de9-124">如需詳細資訊，請參閱 MSDN Library 中的 [system.web.extensions 項目 (ASP.NET 設定結構描述)](https://go.microsoft.com/fwlink/?LinkId=178352) 。</span><span class="sxs-lookup"><span data-stu-id="59de9-124">For more information, see [system.web.extensions Element (ASP.NET Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178352) in the MSDN Library.</span></span>|  
|`system.webServer`|<span data-ttu-id="59de9-125">包含 IIS 項目的區段群組。</span><span class="sxs-lookup"><span data-stu-id="59de9-125">Section group that contains IIS elements.</span></span> <span data-ttu-id="59de9-126">如需詳細資訊，請參閱 MSDN Library 中的 [system.webServer 區段群組 \[IIS 7 設定結構描述\]](https://go.microsoft.com/fwlink/?LinkId=178353)。</span><span class="sxs-lookup"><span data-stu-id="59de9-126">For more information, see [system.webServer Section Group \[IIS 7 Settings Schema\]](https://go.microsoft.com/fwlink/?LinkId=178353) in the MSDN Library.</span></span>|  
|`system.serviceModel`|<span data-ttu-id="59de9-127">WCF 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-127">WCF element.</span></span> <span data-ttu-id="59de9-128">如需詳細資訊，請參閱 [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) MSDN Library 中的。</span><span class="sxs-lookup"><span data-stu-id="59de9-128">For more information, see [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) in the MSDN Library.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="59de9-129">.NET Framework 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-129">.NET Framework element.</span></span> <span data-ttu-id="59de9-130">如需詳細資訊，請參閱 MSDN Library 中的[ \<system.diagnostics> 元素](https://go.microsoft.com/fwlink/?LinkId=178355)。</span><span class="sxs-lookup"><span data-stu-id="59de9-130">For more information, see [\<system.diagnostics> Element](https://go.microsoft.com/fwlink/?LinkId=178355) in the MSDN Library.</span></span>|  
|`appSettings`|<span data-ttu-id="59de9-131">ASP.NET 元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-131">ASP.NET element.</span></span> <span data-ttu-id="59de9-132">如需詳細資訊，請參閱 MSDN Library 中的 [appSettings 項目 (一般設定結構描述)](https://go.microsoft.com/fwlink/?LinkId=178356) 。</span><span class="sxs-lookup"><span data-stu-id="59de9-132">For more information, see [appSettings Element (General Settings Schema)](https://go.microsoft.com/fwlink/?LinkId=178356) in the MSDN Library.</span></span>|  
  
## <a name="masterdataservices-element"></a><span data-ttu-id="59de9-133">masterDataServices 元素</span><span class="sxs-lookup"><span data-stu-id="59de9-133">masterDataServices Element</span></span>  
 <span data-ttu-id="59de9-134">**\<masterDataServices>** 元素是用來將 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服務連接到資料庫的自訂元素 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="59de9-134">The **\<masterDataServices>** element is a custom element that is used to connect a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web service to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="59de9-135">語法</span><span class="sxs-lookup"><span data-stu-id="59de9-135">Syntax</span></span>  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a><span data-ttu-id="59de9-136">元素和屬性</span><span class="sxs-lookup"><span data-stu-id="59de9-136">Elements and Attributes</span></span>  
  
|<span data-ttu-id="59de9-137">項目</span><span class="sxs-lookup"><span data-stu-id="59de9-137">Item</span></span>|<span data-ttu-id="59de9-138">描述</span><span class="sxs-lookup"><span data-stu-id="59de9-138">Description</span></span>|  
|----------|-----------------|  
|`instance`|<span data-ttu-id="59de9-139">子元素。</span><span class="sxs-lookup"><span data-stu-id="59de9-139">Child element.</span></span> <span data-ttu-id="59de9-140">包含指定 Web 服務和資料庫連接字串之資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="59de9-140">Contains attributes that specify information for the Web service and database connection string.</span></span>|  
|`virtualPath`|<span data-ttu-id="59de9-141">屬性。</span><span class="sxs-lookup"><span data-stu-id="59de9-141">Attribute.</span></span> <span data-ttu-id="59de9-142">指定 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式和服務的路徑。</span><span class="sxs-lookup"><span data-stu-id="59de9-142">Specifies the virtual path of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and service.</span></span> <span data-ttu-id="59de9-143">這會對應到 `path` IIS ApplicationHost.config 檔案中專案底下元素的屬性 **\<application>** **\<site>** 。</span><span class="sxs-lookup"><span data-stu-id="59de9-143">This corresponds to the `path` attribute of the **\<application>** element under the **\<site>** element in the IIS ApplicationHost.config file.</span></span>|  
|`siteName`|<span data-ttu-id="59de9-144">屬性。</span><span class="sxs-lookup"><span data-stu-id="59de9-144">Attribute.</span></span> <span data-ttu-id="59de9-145">指定主控 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式和服務之網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="59de9-145">Specifies the name of the site that hosts the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application and service.</span></span> <span data-ttu-id="59de9-146">這會對應到 `name` **\<site>** IIS ApplicationHost.config 檔案中底下元素的屬性 **\<sites>** 。</span><span class="sxs-lookup"><span data-stu-id="59de9-146">This corresponds to the `name` attribute of the **\<site>** element under **\<sites>** in the IIS ApplicationHost.config file.</span></span>|  
|`connectionName`|<span data-ttu-id="59de9-147">屬性。</span><span class="sxs-lookup"><span data-stu-id="59de9-147">Attribute.</span></span> <span data-ttu-id="59de9-148">指定要使用之連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="59de9-148">Specifies the name of the connection to use.</span></span> <span data-ttu-id="59de9-149">這會對應至 Web.config 之專案底下 `name` 元素的屬性 **\<add>** **\<connectionStrings>** 。</span><span class="sxs-lookup"><span data-stu-id="59de9-149">This corresponds to the `name` attribute of the **\<add>** element under the **\<connectionStrings>** element in Web.config.</span></span>|  
|`serviceName`|<span data-ttu-id="59de9-150">屬性。</span><span class="sxs-lookup"><span data-stu-id="59de9-150">Attribute.</span></span> <span data-ttu-id="59de9-151">指定 Web 服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="59de9-151">Specifies the name of the Web service.</span></span> <span data-ttu-id="59de9-152">這會對應至 Web.config 之專案底下 `name` 元素的屬性 **\<service>** **\<services>** 。</span><span class="sxs-lookup"><span data-stu-id="59de9-152">This corresponds to the `name` attribute of the **\<service>** element under the **\<services>** element in Web.config.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="59de9-153">範例</span><span class="sxs-lookup"><span data-stu-id="59de9-153">Example</span></span>  
 <span data-ttu-id="59de9-154">下列範例示範使用 MDSDB 指定之連接字串的 Contoso 網站和 /MDS 路徑上一項名為 MDS1 的服務。</span><span class="sxs-lookup"><span data-stu-id="59de9-154">The following example demonstrates a service named MDS1 on the Contoso site and /MDS path using a connection string specified by MDSDB.</span></span>  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
