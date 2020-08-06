---
title: 套件設定 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d22dbfedcf4cf7084e1667586f9774926f3b2a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606979"
---
# <a name="package-configurations"></a><span data-ttu-id="5fa62-102">封裝組態</span><span class="sxs-lookup"><span data-stu-id="5fa62-102">Package Configurations</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="5fa62-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供可用在執行階段更新屬性值的套件組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides package configurations that you can use to update the values of properties at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fa62-104">組態可用於封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="5fa62-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="5fa62-105">參數是用來取代專案部署模型的組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="5fa62-106">專案部署模型讓您能將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5fa62-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="5fa62-107">如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5fa62-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="5fa62-108">組態是您加入已完成封裝的一組屬性/值配對。</span><span class="sxs-lookup"><span data-stu-id="5fa62-108">A configuration is a property/value pair that you add to a completed package.</span></span> <span data-ttu-id="5fa62-109">一般而言，您建立封裝、在封裝開發期間設定封裝物件的屬性，然後將組態加入至封裝。</span><span class="sxs-lookup"><span data-stu-id="5fa62-109">Typically, you create a package set properties on the package objects during package development, and then add the configuration to the package.</span></span> <span data-ttu-id="5fa62-110">當封裝執行時，它會從組態取得新的屬性值；</span><span class="sxs-lookup"><span data-stu-id="5fa62-110">When the package runs, it gets the new values of the property from the configuration.</span></span> <span data-ttu-id="5fa62-111">舉例來說，經由使用組態，您可以變更連接管理員的連接字串，或更新變數的值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-111">For example, by using a configuration, you can change the connection string of a connection manager, or update the value of a variable.</span></span>  
  
 <span data-ttu-id="5fa62-112">封裝組態提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="5fa62-112">Package configurations provide the following benefits:</span></span>  
  
-   <span data-ttu-id="5fa62-113">組態會使將封裝從開發環境移至實際執行環境更為容易。</span><span class="sxs-lookup"><span data-stu-id="5fa62-113">Configurations make it easier to move packages from a development environment to a production environment.</span></span> <span data-ttu-id="5fa62-114">例如，組態可以更新來源檔案的路徑，或者變更資料庫或伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fa62-114">For example, a configuration can update the path of a source file, or change the name of a database or server.</span></span>  
  
-   <span data-ttu-id="5fa62-115">組態在您將封裝部署到許多不同的伺服器時非常有用。</span><span class="sxs-lookup"><span data-stu-id="5fa62-115">Configurations are useful when you deploy packages to many different servers.</span></span> <span data-ttu-id="5fa62-116">例如，組態中每個已部署封裝的變數都可包含不同的磁碟空間值，如果可用磁碟空間不符合這個值，封裝就不會執行。</span><span class="sxs-lookup"><span data-stu-id="5fa62-116">For example, a variable in the configuration for each deployed package can contain a different disk space value, and if the available disk space does not meet this value, the package does not run.</span></span>  
  
-   <span data-ttu-id="5fa62-117">組態使封裝更有彈性。</span><span class="sxs-lookup"><span data-stu-id="5fa62-117">Configurations make packages more flexible.</span></span> <span data-ttu-id="5fa62-118">例如，組態可以更新屬性運算式中使用的變數值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-118">For example, a configuration can update the value of a variable that is used in a property expression.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="5fa62-119">支援使用幾種不同的方法儲存封裝組態，例如 XML 檔案、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中的資料表，以及環境和封裝變數。</span><span class="sxs-lookup"><span data-stu-id="5fa62-119">supports several different methods of storing package configurations, such as XML files, tables in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and environment and package variables.</span></span>  
  
 <span data-ttu-id="5fa62-120">每個組態都是屬性/值配對。</span><span class="sxs-lookup"><span data-stu-id="5fa62-120">Each configuration is a property/value pair.</span></span> <span data-ttu-id="5fa62-121">XML 組態檔和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態類型可以包含多重組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-121">The XML configuration file and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration types can include multiple configurations.</span></span>  
  
 <span data-ttu-id="5fa62-122">當您建立用以安裝封裝的封裝部署公用程式時，會包含這些組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-122">The configurations are included when you create a package deployment utility for installing packages.</span></span> <span data-ttu-id="5fa62-123">在安裝封裝時，您可以在封裝的安裝過程中更新這些組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-123">When you install the packages, the configurations can be updated as a step in the package installation.</span></span>  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a><span data-ttu-id="5fa62-124">了解如何在執行階段套用封裝組態</span><span class="sxs-lookup"><span data-stu-id="5fa62-124">Understanding How Package Configurations Are Applied at Run Time</span></span>  
 <span data-ttu-id="5fa62-125">當您使用 **dtexec** 命令提示字元公用程式 (dtexec.exe) 來執行部署的封裝時，此公用程式會套用封裝組態兩次。</span><span class="sxs-lookup"><span data-stu-id="5fa62-125">When you use the **dtexec** command prompt utility (dtexec.exe) to run a deployed package, the utility applies package configurations twice.</span></span> <span data-ttu-id="5fa62-126">當此公用程式套用您在命令列上所指定之選項的前後，都會套用組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-126">The utility applies configurations both before and after it applies the options that you specified on command line.</span></span>  
  
 <span data-ttu-id="5fa62-127">當此公用程式載入及執行此封裝時，事件會依照下列順序發生：</span><span class="sxs-lookup"><span data-stu-id="5fa62-127">As the utility loads and runs the package, events occur in the following order:</span></span>  
  
1.  <span data-ttu-id="5fa62-128">**dtexec** 公用程式會載入此封裝。</span><span class="sxs-lookup"><span data-stu-id="5fa62-128">The **dtexec** utility loads the package.</span></span>  
  
2.  <span data-ttu-id="5fa62-129">此公用程式會套用您在設計階段於封裝內所指定的組態，而且會依照封裝內所指定的順序</span><span class="sxs-lookup"><span data-stu-id="5fa62-129">The utility applies the configurations that were specified in the package at design time and in the order that is specified in the package.</span></span> <span data-ttu-id="5fa62-130">(唯一的例外是父封裝變數組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-130">(The one exception to this is the Parent Package Variables configurations.</span></span> <span data-ttu-id="5fa62-131">此公用程式只會在稍後於處理序中套用這些組態一次)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-131">The utility applies these configurations only once and later in the process.)</span></span>  
  
3.  <span data-ttu-id="5fa62-132">然後此公用程式會套用您在命令列上所指定的任何選項。</span><span class="sxs-lookup"><span data-stu-id="5fa62-132">The utility then applies any options that you specified on the command line.</span></span>  
  
4.  <span data-ttu-id="5fa62-133">然後此公用程式會重新載入您在設計階段於封裝內所指定的組態，而且會依照封裝內所指定的順序</span><span class="sxs-lookup"><span data-stu-id="5fa62-133">The utility then reloads the configurations that were specified in the package at design time and in the order specified in the package.</span></span> <span data-ttu-id="5fa62-134">(同樣地，此規則的例外是父封裝變數組態)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-134">(Again, the exception to this rule is the Parent Package Variables configurations).</span></span> <span data-ttu-id="5fa62-135">此公用程式會使用您所指定的任何命令列選項來重新載入組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-135">The utility uses any command-line options that were specified to reload the configurations.</span></span> <span data-ttu-id="5fa62-136">因此，可能會從不同的位置重新載入不同的值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-136">Therefore, different values might be reloaded from a different location.</span></span>  
  
5.  <span data-ttu-id="5fa62-137">此公用程式會套用父封裝變數組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-137">The utility applies the Parent Package Variable configurations.</span></span>  
  
6.  <span data-ttu-id="5fa62-138">此公用程式會執行此封裝。</span><span class="sxs-lookup"><span data-stu-id="5fa62-138">The utility runs the package.</span></span>  
  
 <span data-ttu-id="5fa62-139">**dtexec** 公用程式套用組態的方式會影響下列命令列選項：</span><span class="sxs-lookup"><span data-stu-id="5fa62-139">The way in which the **dtexec** utility applies configurations affects the following command-line options:</span></span>  
  
-   <span data-ttu-id="5fa62-140">您可以在執行階段使用 **/Connection** 或 **/Set** 選項，從不同於設計時所指定的位置載入封裝組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-140">You can use the **/Connection** or **/Set** option at run time to load package configurations from a location other than the location that you specified at design time.</span></span>  
  
-   <span data-ttu-id="5fa62-141">您可以使用 **/ConfigFile** 選項來載入您並未在設計階段指定的其他組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-141">You can use the **/ConfigFile** option to load additional configurations that you did not specify at design time.</span></span>  
  
 <span data-ttu-id="5fa62-142">但是，這些命令列選項確實有一些限制：</span><span class="sxs-lookup"><span data-stu-id="5fa62-142">However, these command-line options do have some restrictions:</span></span>  
  
-   <span data-ttu-id="5fa62-143">您不能使用 **/Set** 或 **/Connection** 選項來覆寫同樣由組態所設定的單一值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-143">You cannot use the **/Set** or the **/Connection** option to override single values that are also set by a configuration.</span></span>  
  
-   <span data-ttu-id="5fa62-144">您不能使用 **/ConfigFile** 選項來載入可取代您在設計階段指定之組態的組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-144">You cannot use the **/ConfigFile** option to load configurations that replace the configurations that you specified at design time.</span></span>  
  
 <span data-ttu-id="5fa62-145">如需這些選項的詳細資訊，以及這些選項的行為 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 在和舊版之間的差異，請參閱[SQL Server 2014 中 Integration Services 功能的行為變更](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-145">For more information about these options, and how the behavior of these options differs between [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] and earlier versions, see [Behavior Changes to Integration Services Features in SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
## <a name="package-configuration-types"></a><span data-ttu-id="5fa62-146">封裝組態類型</span><span class="sxs-lookup"><span data-stu-id="5fa62-146">Package Configuration Types</span></span>  
 <span data-ttu-id="5fa62-147">下表描述封裝組態類型。</span><span class="sxs-lookup"><span data-stu-id="5fa62-147">The following table describes the package configuration types.</span></span>  
  
|<span data-ttu-id="5fa62-148">類型</span><span class="sxs-lookup"><span data-stu-id="5fa62-148">Type</span></span>|<span data-ttu-id="5fa62-149">描述</span><span class="sxs-lookup"><span data-stu-id="5fa62-149">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5fa62-150">XML 組態檔</span><span class="sxs-lookup"><span data-stu-id="5fa62-150">XML configuration file</span></span>|<span data-ttu-id="5fa62-151">XML 檔案包含組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-151">An XML file contains the configurations.</span></span> <span data-ttu-id="5fa62-152">XML 檔案可以包含多重組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-152">The XML file can include multiple configurations.</span></span>|  
|<span data-ttu-id="5fa62-153">環境變數</span><span class="sxs-lookup"><span data-stu-id="5fa62-153">Environment variable</span></span>|<span data-ttu-id="5fa62-154">環境變數包含組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-154">An environment variable contains the configuration.</span></span>|  
|<span data-ttu-id="5fa62-155">登錄項目</span><span class="sxs-lookup"><span data-stu-id="5fa62-155">Registry entry</span></span>|<span data-ttu-id="5fa62-156">登錄項目包含組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-156">A Registry entry contains the configuration.</span></span>|  
|<span data-ttu-id="5fa62-157">父封裝變數</span><span class="sxs-lookup"><span data-stu-id="5fa62-157">Parent package variable</span></span>|<span data-ttu-id="5fa62-158">封裝中的變數包含組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-158">A variable in the package contains the configuration.</span></span> <span data-ttu-id="5fa62-159">這個組態類型通常用來更新子封裝中的屬性。</span><span class="sxs-lookup"><span data-stu-id="5fa62-159">This configuration type is typically used to update properties in child packages.</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="5fa62-160">資料表</span><span class="sxs-lookup"><span data-stu-id="5fa62-160">table</span></span>|<span data-ttu-id="5fa62-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中的資料表包含組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-161">A table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database contains the configuration.</span></span> <span data-ttu-id="5fa62-162">資料表可以包含多重組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-162">The table can include multiple configurations.</span></span>|  
  
### <a name="xml-configuration-files"></a><span data-ttu-id="5fa62-163">XML 組態檔</span><span class="sxs-lookup"><span data-stu-id="5fa62-163">XML Configuration Files</span></span>  
 <span data-ttu-id="5fa62-164">如果選取 [XML 組態檔]  組態類型，您可以建立新的組態檔、重複使用現有的檔案並加入新組態，或者重複使用現有的檔案但覆寫現有的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="5fa62-164">If you select the **XML configuration file** configuration type, you can create a new configuration file, reuse an existing file and add new configurations, or reuse an existing file but overwrite existing file content.</span></span>  
  
 <span data-ttu-id="5fa62-165">XML 組態檔包含兩個區段：</span><span class="sxs-lookup"><span data-stu-id="5fa62-165">An XML configuration file includes two sections:</span></span>  
  
-   <span data-ttu-id="5fa62-166">包含組態檔相關資訊的標題。</span><span class="sxs-lookup"><span data-stu-id="5fa62-166">A heading that contains information about the configuration file.</span></span> <span data-ttu-id="5fa62-167">此元素包含諸如檔案建立時間和產生檔案之使用者的姓名等屬性。</span><span class="sxs-lookup"><span data-stu-id="5fa62-167">This element includes attributes such as when the file was created and the name of the person who generated the file.</span></span>  
  
-   <span data-ttu-id="5fa62-168">包含每個組態相關資訊的組態項目。</span><span class="sxs-lookup"><span data-stu-id="5fa62-168">Configuration elements that contain information about each configuration.</span></span> <span data-ttu-id="5fa62-169">此元素包含諸如屬性 (Property) 路徑和屬性 (Property) 的已設定值等屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-169">This element includes attributes such as the property path and the configured value of a property.</span></span>  
  
 <span data-ttu-id="5fa62-170">下面的 XML 程式碼會示範 XML 組態檔的語法。</span><span class="sxs-lookup"><span data-stu-id="5fa62-170">The following XML code demonstrates the syntax of an XML configuration file.</span></span> <span data-ttu-id="5fa62-171">這個範例會示範名為 `MyVar`之整數變數的 Value 屬性組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-171">This example shows a configuration for the Value property of an integer variable named `MyVar`.</span></span>  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a><span data-ttu-id="5fa62-172">登錄項目</span><span class="sxs-lookup"><span data-stu-id="5fa62-172">Registry Entry</span></span>  
 <span data-ttu-id="5fa62-173">如果您想使用登錄項目儲存組態，可以使用現有的機碼或在 HKEY_CURRENT_USER 中建立新的機碼。</span><span class="sxs-lookup"><span data-stu-id="5fa62-173">If you want to use a Registry entry to store the configuration, you can either use an existing key or create a new key in HKEY_CURRENT_USER.</span></span> <span data-ttu-id="5fa62-174">您所使用的登錄機碼必須具有名為 `Value` 的值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-174">The Registry key that you use must have a value named `Value`.</span></span> <span data-ttu-id="5fa62-175">該值可以是 DWORD 或字串。</span><span class="sxs-lookup"><span data-stu-id="5fa62-175">The value can be a DWORD or a string.</span></span>  
  
 <span data-ttu-id="5fa62-176">如果您選取 [登錄項目]  組態類型，就要在 [登錄項目] 方塊中輸入登錄機碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fa62-176">If you select the **Registry entry** configuration type, you type the name of the Registry key in the Registry entry box.</span></span> <span data-ttu-id="5fa62-177">格式為 \<registry key>。</span><span class="sxs-lookup"><span data-stu-id="5fa62-177">The format is \<registry key>.</span></span> <span data-ttu-id="5fa62-178">如果想要使用不是在 HKEY_CURRENT_USER 根目錄的登錄機碼，請使用 \<Registry key\registry key\\...> 格式識別該機碼。</span><span class="sxs-lookup"><span data-stu-id="5fa62-178">If you want to use a Registry key that is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span> <span data-ttu-id="5fa62-179">例如，若要使用位於 SSISPackages 中的 MyPackage 機碼，請輸入 `SSISPackages\MyPackage`。</span><span class="sxs-lookup"><span data-stu-id="5fa62-179">For example, to use the MyPackage key located in SSISPackages, type `SSISPackages\MyPackage`.</span></span>  
  
### <a name="sql-server"></a><span data-ttu-id="5fa62-180">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5fa62-180">SQL Server</span></span>  
 <span data-ttu-id="5fa62-181">如果選取 [SQL Server]  組態類型，則需要指定要儲存組態之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="5fa62-181">If you select the **SQL Server** configuration type, you specify the connection to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database in which you want to store the configurations.</span></span> <span data-ttu-id="5fa62-182">您可以將組態儲存至現有的資料表，或者在指定的資料庫中建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="5fa62-182">You can save the configurations to an existing table or create a new table in the specified database.</span></span>  
  
 <span data-ttu-id="5fa62-183">下列 SQL 陳述式顯示 [封裝組態精靈] 提供的預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5fa62-183">The following SQL statement shows the default CREATE TABLE statement that the Package Configuration Wizard provides.</span></span>  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 <span data-ttu-id="5fa62-184">您提供給組態的名稱為 **ConfigurationFilter** 資料行中儲存的值。</span><span class="sxs-lookup"><span data-stu-id="5fa62-184">The name that you provide for the configuration is the value stored in the **ConfigurationFilter** column.</span></span>  
  
## <a name="direct-and-indirect-configurations"></a><span data-ttu-id="5fa62-185">直接和間接組態</span><span class="sxs-lookup"><span data-stu-id="5fa62-185">Direct and Indirect Configurations</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="5fa62-186">提供直接和間接組態。</span><span class="sxs-lookup"><span data-stu-id="5fa62-186">provides direct and indirect configurations.</span></span> <span data-ttu-id="5fa62-187">如果您直接指定組態， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 便會在組態項目和封裝物件屬性之間建立直接的連結。</span><span class="sxs-lookup"><span data-stu-id="5fa62-187">If you specify configurations directly, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] creates a direct link between the configuration item and the package object property.</span></span> <span data-ttu-id="5fa62-188">來源的位置沒有變更時，使用直接組態是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="5fa62-188">Direct configurations are a better choice when the location of the source does not change.</span></span> <span data-ttu-id="5fa62-189">例如，如果您確定封裝中的所有部署都使用相同的檔案路徑，便可指定 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="5fa62-189">For example, if you are sure that all deployments in the package use the same file path, you can specify an XML configuration file.</span></span>  
  
 <span data-ttu-id="5fa62-190">間接組態會使用環境變數。</span><span class="sxs-lookup"><span data-stu-id="5fa62-190">Indirect configurations use environment variables.</span></span> <span data-ttu-id="5fa62-191">與直接指定組態設定的方法不同，間接組態會指向包含組態值的環境變數。</span><span class="sxs-lookup"><span data-stu-id="5fa62-191">Instead of specifying the configuration setting directly, the configuration points to an environment variable, which in turn contains the configuration value.</span></span> <span data-ttu-id="5fa62-192">如果組態的位置可以針對封裝的每個部署變更，則使用間接組態是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="5fa62-192">Using indirect configurations is a better choice when the location of the configuration can change for each deployment of a package.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5fa62-193">相關工作</span><span class="sxs-lookup"><span data-stu-id="5fa62-193">Related Tasks</span></span>  
 [<span data-ttu-id="5fa62-194">建立套件設定</span><span class="sxs-lookup"><span data-stu-id="5fa62-194">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a><span data-ttu-id="5fa62-195">相關內容</span><span class="sxs-lookup"><span data-stu-id="5fa62-195">Related Content</span></span>  
  
-   <span data-ttu-id="5fa62-196">msdn.microsoft.com 上的技術文件： [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643)(了解 Integration Services 封裝組態)</span><span class="sxs-lookup"><span data-stu-id="5fa62-196">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="5fa62-197">Www.sqlis.com 上的 Blog 專案，[以程式碼套件設定建立封裝](https://go.microsoft.com/fwlink/?LinkId=217663)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-197">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="5fa62-198">Blog 專案， [API 範例-在 blogs.msdn.com 上以程式設計方式將設定檔新增至套件](https://go.microsoft.com/fwlink/?LinkId=217664)。</span><span class="sxs-lookup"><span data-stu-id="5fa62-198">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
  
