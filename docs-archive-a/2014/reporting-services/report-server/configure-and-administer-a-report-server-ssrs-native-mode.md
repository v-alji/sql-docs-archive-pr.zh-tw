---
title: 設定和管理報表伺服器 (SSRS 原生模式) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5164fd2f9170cb092a45394f64f06d7622253f2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597599"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a><span data-ttu-id="fde76-102">設定和管理報表伺服器 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="fde76-102">Configure and Administer a Report Server (SSRS Native Mode)</span></span>
  <span data-ttu-id="fde76-103">本主題摘要列出您可以用來設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的方法，</span><span class="sxs-lookup"><span data-stu-id="fde76-103">This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fde76-104">也包含了主題清單，用來解釋如何設定特定的元件、功能或伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="fde76-104">It also includes a list of topics that explain how to configure specific components, features, or server capabilities.</span></span> <span data-ttu-id="fde76-105">若要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，您可以：</span><span class="sxs-lookup"><span data-stu-id="fde76-105">To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="fde76-106">使用 [Reporting Services 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="fde76-106">Use the Reporting Services Configuration Manager.</span></span> <span data-ttu-id="fde76-107">本節中的許多主題都包含了有關如何透過這個工具來設定特定功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="fde76-107">Many of the topics in this section contain information about how to configure specific features through this tool.</span></span>  
  
-   <span data-ttu-id="fde76-108">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來自訂伺服器屬性、啟用 [我的報表]、啟用追蹤記錄及設定網站範圍的預設值。</span><span class="sxs-lookup"><span data-stu-id="fde76-108">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to customize server properties, enable My Reports, enable trace logs, and set site-wide defaults.</span></span> <span data-ttu-id="fde76-109">如需網站設定的詳細資訊，請參閱 Management Studio 的 [Reporting Services 報表伺服器 &#40;原生模式&#41;](reporting-services-report-server-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="fde76-109">For more information about site settings, see [Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) for Management Studio.</span></span> <span data-ttu-id="fde76-110">請注意，您可以建立並執行以程式設計方式設定伺服器屬性的指令碼。</span><span class="sxs-lookup"><span data-stu-id="fde76-110">Note that you can create and run script that sets server properties programmatically.</span></span> <span data-ttu-id="fde76-111">如需詳細資訊，請參閱 [編寫部署和管理工作的指令碼](../tools/script-deployment-and-administrative-tasks.md) 和 [報表伺服器系統屬性](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="fde76-111">For more information, see [Script Deployment and Administrative Tasks](../tools/script-deployment-and-administrative-tasks.md) and [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).</span></span>  
  
-   <span data-ttu-id="fde76-112">使用報表管理員來授與存取報表伺服器的權限。</span><span class="sxs-lookup"><span data-stu-id="fde76-112">Use Report Manager to grant permissions to access the report server.</span></span> <span data-ttu-id="fde76-113">這些權限是透過您針對每個使用者或群組帳戶定義的角色指派傳達的。</span><span class="sxs-lookup"><span data-stu-id="fde76-113">Permissions are conveyed through role assignments that you define for each user or group account.</span></span> <span data-ttu-id="fde76-114">如需詳細資訊，請參閱[角色與權限 &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fde76-114">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="fde76-115">(選擇性) 修改組態檔來變更應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fde76-115">Optionally, modify configuration files to change application settings.</span></span> <span data-ttu-id="fde76-116">如需每個檔案和修改它們之指導方針的詳細資訊，請參閱 [Reporting Services Configuration Files](reporting-services-configuration-files.md)(Reporting Services 組態檔)。</span><span class="sxs-lookup"><span data-stu-id="fde76-116">For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fde76-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="fde76-117">In This Section</span></span>  
 [<span data-ttu-id="fde76-118">設定報表伺服器 URL &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-118">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-119">描述如何定義用來存取報表伺服器和報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="fde76-119">Describes how to define the URLs used to access the report server and Report Manager.</span></span>  
  
 [<span data-ttu-id="fde76-120">設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-120">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-121">提供如何修改服務帳戶和密碼的建議與步驟。</span><span class="sxs-lookup"><span data-stu-id="fde76-121">Provides recommendations and steps on how to modify service account and password.</span></span>  
  
 [<span data-ttu-id="fde76-122">建立報表伺服器資料庫 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-122">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-123">描述如何建立儲存伺服器中繼資料和物件所需的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="fde76-123">Describes how to create a report server database, required for storing server metadata and objects.</span></span>  
  
 [<span data-ttu-id="fde76-124">設定報表伺服器資料庫連接 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-124">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-125">描述如何修改報表伺服器用來連接到報表伺服器資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="fde76-125">Describes how to modify the connection string used by the report server to connect to the report server database.</span></span>  
  
 [<span data-ttu-id="fde76-126">針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-126">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-127">描述如何設定報表伺服器，以支援電子郵件報表散發。</span><span class="sxs-lookup"><span data-stu-id="fde76-127">Describes how to configure a report server to support e-mail report distribution.</span></span>  
  
 [<span data-ttu-id="fde76-128">設定自動執行帳戶 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-128">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="fde76-129">描述如何設定使用者帳戶以自動模式處理報表。</span><span class="sxs-lookup"><span data-stu-id="fde76-129">Describes how to configure a user account to process reports in unattended mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde76-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fde76-130">See Also</span></span>  
 <span data-ttu-id="fde76-131">[設定報表產生器存取](configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="fde76-131">[Configure Report Builder Access](configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="fde76-132">[Reporting Services 組態檔](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="fde76-132">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="fde76-133">[Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="fde76-133">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="fde76-134">[Reporting Services 的安全性與保護](../security/reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="fde76-134">[Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="fde76-135">Reporting Services 報表伺服器 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="fde76-135">Reporting Services Report Server &#40;Native Mode&#41;</span></span>](reporting-services-report-server-native-mode.md)  
  
  
