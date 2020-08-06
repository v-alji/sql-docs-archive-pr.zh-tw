---
title: 資料庫 (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb8f1841e980279d6051e3393efdf06df238f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606623"
---
# <a name="database-ssrs-native-mode"></a><span data-ttu-id="4058f-102">資料庫 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="4058f-102">Database (SSRS Native Mode)</span></span>
  <span data-ttu-id="4058f-103">使用 [資料庫] 頁面，即可建立和設定報表伺服器資料庫，以便提供一個或多個報表伺服器執行個體的內部儲存位置。</span><span class="sxs-lookup"><span data-stu-id="4058f-103">Use the Database page to create and configure the report server databases that provide internal storage for one or more report server instances.</span></span> <span data-ttu-id="4058f-104">如果您要設定報表伺服器使用遠端報表伺服器資料庫，您必須使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員建立此資料庫。</span><span class="sxs-lookup"><span data-stu-id="4058f-104">If you are configuring a report server to use a remote report server database, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to create the database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="4058f-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="4058f-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="4058f-106">建立報表伺服器資料庫和設定連接是多重步驟的程序。</span><span class="sxs-lookup"><span data-stu-id="4058f-106">Creating a report server database and configuring the connection is a multi-step process.</span></span> <span data-ttu-id="4058f-107">此頁面會提供每一種工作類型的精靈，以引導您執行步驟。</span><span class="sxs-lookup"><span data-stu-id="4058f-107">To guide you through the steps, this page provides Wizards for each type of task.</span></span> <span data-ttu-id="4058f-108">將會為您建立或更新權限和登入。</span><span class="sxs-lookup"><span data-stu-id="4058f-108">Permissions and logins are created or updated for you.</span></span> <span data-ttu-id="4058f-109">您可以在 [進度] 頁面中監視每一個步驟的狀態。</span><span class="sxs-lookup"><span data-stu-id="4058f-109">You can monitor the status of each step in the Progress page.</span></span> <span data-ttu-id="4058f-110">如果發生錯誤，您可以按一下此錯誤，以取得如何解決它的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4058f-110">If an error occurs, you can click the error for information on how to resolve it.</span></span>  
  
 <span data-ttu-id="4058f-111">報表伺服器資料庫必須支援特定的伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="4058f-111">A report server database must support a specific server mode.</span></span> <span data-ttu-id="4058f-112">預設的模式為原生模式，但如果您是在較大的 SharePoint 產品或技術部署中執行報表伺服器，也可以建立使用 SharePoint 整合模式的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="4058f-112">The default mode is native mode, but you can also create a report server database for SharePoint integrated mode if you are running a report server in a larger deployment of a SharePoint product or technology.</span></span> <span data-ttu-id="4058f-113">如需詳細資訊，請參閱[建立原生模式報表伺服器資料庫 &#40;SSRS 設定管理員&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。</span><span class="sxs-lookup"><span data-stu-id="4058f-113">For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
 <span data-ttu-id="4058f-114">若要開啟此頁面，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並按一下導覽窗格中的 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="4058f-114">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Database** in the navigation pane.</span></span> <span data-ttu-id="4058f-115">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="4058f-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4058f-116">選項</span><span class="sxs-lookup"><span data-stu-id="4058f-116">Options</span></span>  
 <span data-ttu-id="4058f-117">**SQL Server 名稱**</span><span class="sxs-lookup"><span data-stu-id="4058f-117">**SQL Server Name**</span></span>  
 <span data-ttu-id="4058f-118">在目前的報表伺服器資料庫中， **[SQL Server 名稱]** 會指定執行報表伺服器資料庫的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 名稱。</span><span class="sxs-lookup"><span data-stu-id="4058f-118">In Current Report Server Database, **SQL Server Name** specifies the name of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs the report server database.</span></span> <span data-ttu-id="4058f-119">也可以在本機或遠端電腦上使用預設或具名的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4058f-119">You can use a default or named instance on a local or remote computer.</span></span>  
  
 <span data-ttu-id="4058f-120">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="4058f-120">**Database Name**</span></span>  
 <span data-ttu-id="4058f-121">指定儲存伺服器資料之報表伺服器資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4058f-121">Specifies the name of the report server database that stores server data.</span></span>  
  
 <span data-ttu-id="4058f-122">**報表伺服器模式**</span><span class="sxs-lookup"><span data-stu-id="4058f-122">**Report Server Mode**</span></span>  
 <span data-ttu-id="4058f-123">指出報表伺服器資料庫是支援原生模式或 SharePoint 整合模式。</span><span class="sxs-lookup"><span data-stu-id="4058f-123">Indicates whether the report server database supports native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="4058f-124">如需詳細資訊，請參閱[Reporting Services 報表伺服器](../../../2014/reporting-services/reporting-services-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4058f-124">For more information, see [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md).</span></span>  
  
 <span data-ttu-id="4058f-125">**變更資料庫**</span><span class="sxs-lookup"><span data-stu-id="4058f-125">**Change Database**</span></span>  
 <span data-ttu-id="4058f-126">啟動精靈，此精靈會引導您建立或選取報表伺服器資料庫所需的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="4058f-126">Start a wizard that guides you through all of the steps required for creating or selecting a report server database.</span></span>  
  
 <span data-ttu-id="4058f-127">**認證類型**</span><span class="sxs-lookup"><span data-stu-id="4058f-127">**Credential Type**</span></span>  
 <span data-ttu-id="4058f-128">指定報表伺服器用來連接到報表伺服器資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="4058f-128">Specifies credentials that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="4058f-129">您可以指定的認證類型包括服務帳戶、Windows 網域使用者、Windows 本機使用者或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫登入。</span><span class="sxs-lookup"><span data-stu-id="4058f-129">Credential types you can specify include the service account, a Windows domain user, Windows local user, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="4058f-130">如需選取認證的詳細資訊，請參閱[將報表伺服器資料庫連接設定 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4058f-130">For more information about selecting credentials, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="4058f-131">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="4058f-131">**User Name**</span></span>  
 <span data-ttu-id="4058f-132">如果您是使用 Windows 認證，請指定網域使用者帳戶；如果您是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證，請指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="4058f-132">Specifies a domain user account if you are using Windows credentials, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login if you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials.</span></span> <span data-ttu-id="4058f-133">如果您使用 Windows 認證，請以下列格式指定： \* \<domain> \\<帳戶 \> \*。</span><span class="sxs-lookup"><span data-stu-id="4058f-133">If you are using Windows credentials, specify them in this format: *\<domain>\\<account\>*.</span></span>  
  
 <span data-ttu-id="4058f-134">**密碼**</span><span class="sxs-lookup"><span data-stu-id="4058f-134">**Password**</span></span>  
 <span data-ttu-id="4058f-135">指定帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="4058f-135">Specifies the password for the account.</span></span>  
  
 <span data-ttu-id="4058f-136">**變更認證**</span><span class="sxs-lookup"><span data-stu-id="4058f-136">**Change Credentials**</span></span>  
 <span data-ttu-id="4058f-137">啟動精靈，它將會引導您選取不同帳戶或更新用來連接報表伺服器資料庫之帳戶密碼所需的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="4058f-137">Start a wizard that guides you through all of the steps required for selecting a different account or updating the password on the account that is used to connect to the report server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4058f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4058f-138">See Also</span></span>  
 <span data-ttu-id="4058f-139">[建立原生模式報表伺服器資料庫 &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="4058f-139">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="4058f-140">[Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4058f-140">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="4058f-141">[&#40;SSRS 原生模式的報表伺服器資料庫&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4058f-141">[Report Server Database &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="4058f-142">設定報表伺服器資料庫連接 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="4058f-142">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
