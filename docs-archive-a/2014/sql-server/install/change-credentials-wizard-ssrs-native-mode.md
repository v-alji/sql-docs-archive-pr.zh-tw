---
title: " (SSRS 原生模式) 變更認證嚮導 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f2e84ec59f1241a10ce52e597920827f3afbc06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595528"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a><span data-ttu-id="1ad50-102">變更認證精靈 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="1ad50-102">Change Credentials Wizard (SSRS Native Mode)</span></span>
  <span data-ttu-id="1ad50-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員提供了變更認證精靈，可引導您重新設定報表伺服器用來連接報表伺服器資料庫之帳戶的步驟。</span><span class="sxs-lookup"><span data-stu-id="1ad50-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the Change Credentials Wizard to guide you through the steps of reconfiguring the account that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="1ad50-104">當您變更認證時，組態管理員將會在報表伺服器目前使用之報表伺服器資料庫的資料庫伺服器上，更新所有的權限和資料庫登入資訊。</span><span class="sxs-lookup"><span data-stu-id="1ad50-104">When you change credentials, the Configuration Manager will update all permissions and database login information on the database server for the report server database that is actively used by the report server.</span></span>  
  
 <span data-ttu-id="1ad50-105">若要啟動此精靈，請按一下 **組態管理員內 [資料庫] 頁面上的** [變更認證] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1ad50-105">To start the wizard, click **Change Credentials** on the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="1ad50-106">如需如何啟動 Configuration Manager 的指示 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請參閱[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad50-106">For instructions on how to start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="1ad50-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="1ad50-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ad50-108">選項</span><span class="sxs-lookup"><span data-stu-id="1ad50-108">Options</span></span>  
 <span data-ttu-id="1ad50-109">**資料庫伺服器**</span><span class="sxs-lookup"><span data-stu-id="1ad50-109">**Database Server**</span></span>  
 <span data-ttu-id="1ad50-110">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行報表伺服器資料庫之實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ad50-110">Specifies the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that runs the report server database.</span></span>  
  
 <span data-ttu-id="1ad50-111">若要連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，您必須使用有權登入伺服器及更新資料庫資訊的認證。</span><span class="sxs-lookup"><span data-stu-id="1ad50-111">To connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you must use credentials that have permission to log on to the server and update database information.</span></span> <span data-ttu-id="1ad50-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員會使用目前的 Windows 認證，但是如果您沒有登入或資料庫權限，您可以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫登入。</span><span class="sxs-lookup"><span data-stu-id="1ad50-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you can specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
 <span data-ttu-id="1ad50-113">您不能指定不同的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="1ad50-113">You cannot specify different Windows credentials.</span></span> <span data-ttu-id="1ad50-114">如果您想要以不同的 Windows 使用者身分連接，請以該使用者身分登入，然後啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="1ad50-114">If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="1ad50-115">**認證**</span><span class="sxs-lookup"><span data-stu-id="1ad50-115">**Credentials**</span></span>  
 <span data-ttu-id="1ad50-116">指定用來將報表伺服器連接到報表伺服器資料庫的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1ad50-116">Specifies the account by which the report server connects to the report server database.</span></span> <span data-ttu-id="1ad50-117">有效的值包括報表伺服器 Web 服務的服務帳戶、用來主控報表伺服器之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上定義的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 資料庫登入，或是 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1ad50-117">Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login defined on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance you are using to host the report server, or a Windows account.</span></span> <span data-ttu-id="1ad50-118">如果您使用 Windows 帳戶，您可以指定本機帳戶 (\* \<computername> \\<使用者名稱 \> *) 如果報表伺服器和資料庫位於相同的電腦上，或網域使用者帳戶 (* \<domain> \\<username \> \*) （如果它們位於相同網域的不同電腦上）。</span><span class="sxs-lookup"><span data-stu-id="1ad50-118">If you are using a Windows account, you can specify a local account (*\<computername>\\<username\>*) if the report server and the database are on the same computer, or a domain user account (*\<domain>\\<username\>*) if they are on different computers in the same domain.</span></span>  
  
 <span data-ttu-id="1ad50-119">報表伺服器將會建立資料庫登入，並為您指定的帳戶指派資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="1ad50-119">The report server will create a database login and assign database permissions for the account you specify.</span></span>  
  
 <span data-ttu-id="1ad50-120">報表伺服器不會建立帳戶本身。</span><span class="sxs-lookup"><span data-stu-id="1ad50-120">The report server does not create the account itself.</span></span> <span data-ttu-id="1ad50-121">您所指定的帳戶必須已經存在，而且對部署組態必須是有效的。</span><span class="sxs-lookup"><span data-stu-id="1ad50-121">The account you specify must already exist and it must be valid for your deployment configuration.</span></span> <span data-ttu-id="1ad50-122">具體而言，如果資料庫位於遠端電腦上，而且您想要使用 Windows 帳戶，您就必須指定在該電腦上具有登入權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1ad50-122">Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.</span></span>  
  
 <span data-ttu-id="1ad50-123">如果此電腦位於不同的網域或不信任的網域中，請考慮使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫登入。</span><span class="sxs-lookup"><span data-stu-id="1ad50-123">If the computer is in a different or non-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="1ad50-124">如需選擇帳戶的詳細資訊，請參閱[將報表伺服器資料庫連接設定 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad50-124">For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="1ad50-125">**總結**</span><span class="sxs-lookup"><span data-stu-id="1ad50-125">**Summary**</span></span>  
 <span data-ttu-id="1ad50-126">請在執行精靈之前先確認設定。</span><span class="sxs-lookup"><span data-stu-id="1ad50-126">Verify the settings before the wizard runs.</span></span>  
  
 <span data-ttu-id="1ad50-127">**進度和完成**</span><span class="sxs-lookup"><span data-stu-id="1ad50-127">**Progress and Finish**</span></span>  
 <span data-ttu-id="1ad50-128">監視每項工作的進度。</span><span class="sxs-lookup"><span data-stu-id="1ad50-128">Monitor the progress of each task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad50-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad50-129">See Also</span></span>  
 <span data-ttu-id="1ad50-130">[資料庫 &#40;SSRS 原生模式&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1ad50-130">[Database &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1ad50-131">[&#40;SSRS 原生模式的變更資料庫 Wizard&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1ad50-131">[Change Database Wizard &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1ad50-132">[建立原生模式報表伺服器資料庫 &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="1ad50-132">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="1ad50-133">[Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1ad50-133">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="1ad50-134">設定報表伺服器資料庫連接 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="1ad50-134">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
