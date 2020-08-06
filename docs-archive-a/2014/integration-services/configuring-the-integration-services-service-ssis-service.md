---
title: 設定 Integration Services 服務 (SSIS 服務) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70c41377a2c302e1a021c6ade2a9d487579fa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706662"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a><span data-ttu-id="667f2-102">設定 Integration Services 服務 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="667f2-102">Configuring the Integration Services Service (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="667f2-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="667f2-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] <span data-ttu-id="667f2-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="667f2-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="667f2-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="667f2-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務會仰賴組態檔進行設定。</span><span class="sxs-lookup"><span data-stu-id="667f2-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service relies on a configuration file for its settings.</span></span> <span data-ttu-id="667f2-107">根據預設，此設定檔的名稱為 MsDtsSrvr.ini.xml，且檔案位於%ProgramFiles%\Microsoft SQL Server\120\dts\binn 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="667f2-107">By default, the name for this configuration file is MsDtsSrvr.ini.xml, and the file is located in the folder, %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.</span></span>  
  
 <span data-ttu-id="667f2-108">一般來說，您不必為這個組態檔做任何變更，也不必變更此檔案的預設位置。</span><span class="sxs-lookup"><span data-stu-id="667f2-108">Typically, you do not have to make any changes to this configuration file, nor do you have to change the file's default location.</span></span> <span data-ttu-id="667f2-109">但是，如果您的封裝儲存在 [!INCLUDE[ssDE](../includes/ssde-md.md)]的具名執行個體或遠端執行個體中，或是儲存在多個 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體中，您就必須修改此組態檔。</span><span class="sxs-lookup"><span data-stu-id="667f2-109">However, you will have to modify the configuration file if your packages are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)], or in multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="667f2-110">另外，如果您將此組態檔移到預設位置以外的位置，就必須修改指定其檔案位置的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="667f2-110">Also, if you move the configuration file to a location other than the default location, you will have to modify the Registry key that specifies the file location.</span></span>  
  
## <a name="configuration-file-contents"></a><span data-ttu-id="667f2-111">組態檔內容</span><span class="sxs-lookup"><span data-stu-id="667f2-111">Configuration File Contents</span></span>  
 <span data-ttu-id="667f2-112">當您安裝 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]時，安裝程序會針對 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務建立及安裝組態檔。</span><span class="sxs-lookup"><span data-stu-id="667f2-112">When you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the setup process creates and installs the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="667f2-113">此組態檔包含下列設定：</span><span class="sxs-lookup"><span data-stu-id="667f2-113">This configuration file contains the following settings:</span></span>  
  
-   <span data-ttu-id="667f2-114">在服務停止時傳送停止指令給封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-114">Packages are sent a stop command when the service stops.</span></span>  
  
-   <span data-ttu-id="667f2-115">要在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的 [物件總管] 中顯示的 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 根資料夾為 [MSDB] 和 [檔案系統] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="667f2-115">The root folders to display for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in Object Explorer of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] are the MSDB and File System folders.</span></span>  
  
-   <span data-ttu-id="667f2-116">服務所管理之檔案系統中的封裝 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 位於%PROGRAMFILES%\MICROSOFT SQL Server\120\DTS\Packages。</span><span class="sxs-lookup"><span data-stu-id="667f2-116">The packages in the file system that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages are located in %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.</span></span>  
  
 <span data-ttu-id="667f2-117">此組態檔也會指定哪一個 msdb 資料庫包含 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務將會管理的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-117">This configuration file also specifies which msdb database contains the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service will manage.</span></span> <span data-ttu-id="667f2-118">根據預設， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務設定為可管理 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體之 msdb 資料庫中的封裝，該執行個體與 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]同時安裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-118">By default, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="667f2-119">如果 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體並未同時安裝， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務會設定為可管理本機預設 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體之 msdb 資料庫中的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-119">If an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
### <a name="default-configuration-file-example"></a><span data-ttu-id="667f2-120">預設組態檔範例</span><span class="sxs-lookup"><span data-stu-id="667f2-120">Default Configuration File Example</span></span>  
 <span data-ttu-id="667f2-121">下列範例會顯示可指定以下設定的預設組態檔：</span><span class="sxs-lookup"><span data-stu-id="667f2-121">The following example shows a default configuration file that specifies the following settings:</span></span>  
  
-   <span data-ttu-id="667f2-122">當 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務停止時，封裝會停止執行。</span><span class="sxs-lookup"><span data-stu-id="667f2-122">Packages stop running when the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service stops.</span></span>  
  
-   <span data-ttu-id="667f2-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中封裝儲存體的根資料夾為 MSDB 和檔案系統。</span><span class="sxs-lookup"><span data-stu-id="667f2-123">The root folders for package storage in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are MSDB and File System.</span></span>  
  
-   <span data-ttu-id="667f2-124">此服務會管理儲存於本機預設 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體之 msdb 資料庫內的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-124">The service manages packages that are stored in the msdb database of the local, default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="667f2-125">此服務會管理儲存於檔案系統 [封裝] 資料夾內的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-125">The service manages packages that are stored in the file system in the Packages folder.</span></span>  
  
 <span data-ttu-id="667f2-126">**預設組態檔的範例**</span><span class="sxs-lookup"><span data-stu-id="667f2-126">**Example of a Default Configuration File**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a><span data-ttu-id="667f2-127">組態檔的修改</span><span class="sxs-lookup"><span data-stu-id="667f2-127">Modification of the Configuration File</span></span>  
 <span data-ttu-id="667f2-128">您可以修改組態檔，允許封裝在服務停止時繼續執行、在 [物件總管] 中顯示其他根資料夾，或在檔案系統中指定要由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務管理的不同資料夾或其他資料夾。</span><span class="sxs-lookup"><span data-stu-id="667f2-128">You can modify the configuration file to allow packages to continue running if the service stops, to display additional root folders in Object Explorer, or to specify a different folder or additional folders in the file system to be managed by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="667f2-129">例如，您可以建立屬於 `SqlServerFolder` 類型的其他根資料夾來管理其他 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體之 msdb 資料庫中的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-129">For example, you can create additional root folders of type, `SqlServerFolder`, to manage packages in the msdb databases of additional instances of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="667f2-130">某些字元在資料夾名稱中是無效的。</span><span class="sxs-lookup"><span data-stu-id="667f2-130">Some characters are not valid in folder names.</span></span> <span data-ttu-id="667f2-131">資料夾名稱的有效字元是由 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類別 **System.IO.Path** 和 [GetInvalidFilenameChars] \*\*\*\* 欄位所決定。</span><span class="sxs-lookup"><span data-stu-id="667f2-131">Valid characters for folder names are determined by the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] class **System.IO.Path** and the **GetInvalidFilenameChars** field.</span></span> <span data-ttu-id="667f2-132">[GetInvalidFilenameChars]\*\*\*\* 欄位提供無法在傳遞給 **Path** 類別成員之路徑字串引數中指定的平台特定字元陣列。</span><span class="sxs-lookup"><span data-stu-id="667f2-132">The **GetInvalidFilenameChars** field provides a platform-specific array of characters that cannot be specified in path string arguments passed to members of the **Path** class.</span></span> <span data-ttu-id="667f2-133">有效的字元集可能會因檔案系統而不同。</span><span class="sxs-lookup"><span data-stu-id="667f2-133">The set of invalid characters can vary by file system.</span></span> <span data-ttu-id="667f2-134">無效的字元通常包括引號 (")、小於 (<) 字元和縱線 (|) 字元。</span><span class="sxs-lookup"><span data-stu-id="667f2-134">Typically, invalid characters are the quotation mark ("), less than (<) character, and pipe (|) character.</span></span>  
  
 <span data-ttu-id="667f2-135">但是，若要管理儲存在 [!INCLUDE[ssDE](../includes/ssde-md.md)]具名執行個體或遠端執行個體中的封裝，您就必須修改組態檔。</span><span class="sxs-lookup"><span data-stu-id="667f2-135">However, you will have to modify the configuration file to manage packages that are stored in a named instance or a remote instance of [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="667f2-136">如果您未更新組態檔，就無法使用 **中的** 物件總管 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來檢視儲存在具名執行個體或遠端執行個體之 msdb 資料庫中的封裝。</span><span class="sxs-lookup"><span data-stu-id="667f2-136">If you do not update the configuration file, you cannot use **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view packages that are stored in the msdb database on the named instance or the remote instance.</span></span> <span data-ttu-id="667f2-137">如果您嘗試使用 **[物件總管]** 來檢視這些封裝，您會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="667f2-137">If you try to use **Object Explorer** to view these packages, you receive the following error message:</span></span>  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 <span data-ttu-id="667f2-138">若要為 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務修改此組態檔，您可使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="667f2-138">To modify the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, you use a text editor.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="667f2-139">在您修改服務組態檔後，必須重新啟動服務，才能使用更新的服務組態。</span><span class="sxs-lookup"><span data-stu-id="667f2-139">After you modify the service configuration file, you must restart the service to use the updated service configuration.</span></span>  
  
### <a name="modified-configuration-file-example"></a><span data-ttu-id="667f2-140">修改過的組態檔範例</span><span class="sxs-lookup"><span data-stu-id="667f2-140">Modified Configuration File Example</span></span>  
 <span data-ttu-id="667f2-141">下列範例會顯示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的已修改組態檔。</span><span class="sxs-lookup"><span data-stu-id="667f2-141">The following example shows a modified configuration file for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="667f2-142">此檔案適用於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的具名執行個體，該執行個體稱為 `InstanceName` 且位在名為 `ServerName`的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="667f2-142">This file is for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] called `InstanceName` on a server named `ServerName`.</span></span>  
  
 <span data-ttu-id="667f2-143">**SQL Server 具名執行個體之已修改組態檔的範例**</span><span class="sxs-lookup"><span data-stu-id="667f2-143">**Example of a Modified Configuration File for a Named Instance of SQL Server**</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a><span data-ttu-id="667f2-144">組態檔位置的修改</span><span class="sxs-lookup"><span data-stu-id="667f2-144">Modification of the Configuration File Location</span></span>  
<span data-ttu-id="667f2-145">登錄機碼**HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\ServiceConfigFile**會指定服務所使用之設定檔案的位置和名稱 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="667f2-145">The Registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** specifies the location and name for the configuration file that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses.</span></span> <span data-ttu-id="667f2-146">登錄機碼的預設值為**C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**。</span><span class="sxs-lookup"><span data-stu-id="667f2-146">The default value of the Registry key is **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**.</span></span> <span data-ttu-id="667f2-147">您可以更新此登錄機碼的值，以便針對組態檔使用不同的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="667f2-147">You can update the value of the Registry key to use a different name and location for the configuration file.</span></span> <span data-ttu-id="667f2-148">請注意，path (120 中 SQL Server) 的版本號碼 [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 會根據 SQL Server 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="667f2-148">Note that the version number in the path (120 for SQL Server  [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) will vary depending on the SQL Server version.</span></span> 
  
  
> [!CAUTION]  
>  <span data-ttu-id="667f2-149">不當地編輯登錄可能會造成嚴重問題，並導致您必須重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="667f2-149">Incorrectly editing the Registry can cause serious problems that may require you to reinstall your operating system.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="667f2-150">不保證能夠解決不當編輯登錄所產生的問題。</span><span class="sxs-lookup"><span data-stu-id="667f2-150">cannot guarantee that problems resulting from editing the Registry incorrectly can be resolved.</span></span> <span data-ttu-id="667f2-151">在編輯登錄之前，請先備份重要資料。</span><span class="sxs-lookup"><span data-stu-id="667f2-151">Before editing the Registry, back up any valuable data.</span></span> <span data-ttu-id="667f2-152">如需有關如何備份、還原及編輯登錄的詳細資訊，請參閱 [!INCLUDE[msCoName](../includes/msconame-md.md)] 知識庫文件： [Microsoft Windows 登錄說明](https://support.microsoft.com/kb/256986)。</span><span class="sxs-lookup"><span data-stu-id="667f2-152">For information about how to back up, restore, and edit the Registry, see the [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base article, [Description of the Microsoft Windows registry](https://support.microsoft.com/kb/256986).</span></span>  
  
 <span data-ttu-id="667f2-153">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務啟動時會載入組態檔。</span><span class="sxs-lookup"><span data-stu-id="667f2-153">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service loads the configuration file when the service is started.</span></span> <span data-ttu-id="667f2-154">登錄項目如有任何變更，就必須重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="667f2-154">Any changes to the Registry entry require that the service be restarted.</span></span>  
  
  
