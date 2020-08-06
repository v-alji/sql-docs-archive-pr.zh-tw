---
title: 僅限檔案安裝 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ec5c595dce3e292d37117453ccbbc6d19f8b87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700831"
---
# <a name="files-only-installation-reporting-services"></a><span data-ttu-id="b1cc0-102">僅限檔案安裝 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b1cc0-102">Files-Only Installation (Reporting Services)</span></span>
  <span data-ttu-id="b1cc0-103">「僅限檔案安裝」是指安裝程式會建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 程式檔案的資料夾結構、將檔案複製到磁碟、在本機電腦上註冊報表伺服器服務、設定服務帳戶、授與檔案權限給此服務帳戶，並註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 提供者的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-103">*Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI provider.</span></span>  
  
 <span data-ttu-id="b1cc0-104">僅限檔案安裝包含以下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能：報表伺服器服務 (主控報表伺服器 Web 服務、背景處理應用程式和報表管理員)、報表產生器、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 命令列公用程式 (rsconfig.exe、rskeymgmt.exe 和 rs.exe)。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-104">A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe).</span></span> <span data-ttu-id="b1cc0-105">此安裝不會套用到類似 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的共用功能。如果您想要安裝這些功能，則必須將其指定為個別項目。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-105">It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which must be specified as separate items if you want to install them.</span></span>  
  
 <span data-ttu-id="b1cc0-106">與其他安裝模式相較之下，當安裝程式完成時，在僅限檔案模式下安裝的報表伺服器將不會運作。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-106">In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished.</span></span> <span data-ttu-id="b1cc0-107">您必須使用 [Reporting Services 設定管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) 進行其他組態設定，才能讓報表伺服器在線上工作。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-107">Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="when-to-select-files-only-installation-mode"></a><span data-ttu-id="b1cc0-108">何時選取僅限檔案安裝模式</span><span class="sxs-lookup"><span data-stu-id="b1cc0-108">When to Select Files-Only Installation Mode</span></span>  
 <span data-ttu-id="b1cc0-109">當發生以下狀況時，必須執行僅限檔案安裝：</span><span class="sxs-lookup"><span data-stu-id="b1cc0-109">A files-only installation must be performed when:</span></span>  
  
-   <span data-ttu-id="b1cc0-110">您想要將報表伺服器連接到遠端報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-110">You want to connect the report server to a remote report server database.</span></span>  
  
-   <span data-ttu-id="b1cc0-111">您想要將報表伺服器安裝成具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-111">You want to install the report server as a named instance.</span></span>  
  
-   <span data-ttu-id="b1cc0-112">您的部署需求包括使用自訂設定或功能，而且您對於設定伺服器的時機和方式想要擁有完整控制權。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-112">You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.</span></span>  
  
-   <span data-ttu-id="b1cc0-113">正在安裝含有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-113">Installing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="how-to-perform-a-files-only-installation"></a><span data-ttu-id="b1cc0-114">如何執行僅限檔案安裝</span><span class="sxs-lookup"><span data-stu-id="b1cc0-114">How to Perform a Files-Only Installation</span></span>  
 <span data-ttu-id="b1cc0-115">僅限檔案安裝是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的預設值。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-115">Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b1cc0-116">您可以透過命令列或安裝精靈來指定僅限檔案安裝。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-116">You can specify a files-only installation through the command line or in the Installation wizard.</span></span> <span data-ttu-id="b1cc0-117">下列主題提供逐步指示：</span><span class="sxs-lookup"><span data-stu-id="b1cc0-117">The following topics provide step-by-step instructions:</span></span>  
  
-   <span data-ttu-id="b1cc0-118">[從安裝精靈安裝 SQL Server 2014 &#40;安裝程式&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-118">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="b1cc0-119">[從命令提示字元安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-119">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
#### <a name="example-command-line-script"></a><span data-ttu-id="b1cc0-120">命令列指令碼範例</span><span class="sxs-lookup"><span data-stu-id="b1cc0-120">Example Command Line Script</span></span>  
 <span data-ttu-id="b1cc0-121">為了清楚起見，此範例包含 /RSINSTALLMODE="FilesOnlyMode"。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-121">For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode".</span></span> <span data-ttu-id="b1cc0-122">但是，由於僅限檔案模式為預設值，所以當您忽略此設定時，仍然可以得到僅限檔案模式的安裝。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-122">However, because files-only mode is the default, you can omit this and still get a files-only mode installation.</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a><span data-ttu-id="b1cc0-123">安裝精靈</span><span class="sxs-lookup"><span data-stu-id="b1cc0-123">Installation Wizard</span></span>  
 <span data-ttu-id="b1cc0-124">當您在 [特徵選取] 頁面中選取 [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ] 時，安裝程式會提供 [ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態] 頁面，好讓您指定安裝模式。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-124">When you select [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page that enables you to specify the installation mode.</span></span> <span data-ttu-id="b1cc0-125">若要指定僅限檔案安裝，請在 [[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 設定] 頁面上選取 [安裝但不設定報表伺服器]。</span><span class="sxs-lookup"><span data-stu-id="b1cc0-125">To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cc0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cc0-126">See Also</span></span>  
 <span data-ttu-id="b1cc0-127">[驗證 Reporting Services 安裝](verify-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-127">[Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) </span></span>  
 <span data-ttu-id="b1cc0-128">[設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-128">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b1cc0-129">[設定報表伺服器 URL &#40;SSRS 組態管理員&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-129">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b1cc0-130">[&#40;SSRS Configuration Manager 設定報表伺服器資料庫連接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-130">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b1cc0-131">[Sharepoint 2010 和 SharePoint 2013 Reporting Services SharePoint 模式安裝 &#40;&#41;](install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-131">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="b1cc0-132">[安裝 Reporting Services 原生模式報表伺服器](install-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1cc0-132">[Install Reporting Services Native Mode Report Server](install-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="b1cc0-133">Reporting Services 工具</span><span class="sxs-lookup"><span data-stu-id="b1cc0-133">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
