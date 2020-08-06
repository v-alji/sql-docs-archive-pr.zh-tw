---
title: 建立原生模式報表伺服器資料庫 (SSRS 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 06ad4afe3b8d70899d7299f3b4eb7b97eef6ab66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710286"
---
# <a name="create-a-native-mode-report-server-database--ssrs-configuration-manager"></a><span data-ttu-id="ad710-102">建立原生模式報表伺服器資料庫 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="ad710-102">Create a Native Mode Report Server Database  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="ad710-103">原生模式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫進行內部儲存。</span><span class="sxs-lookup"><span data-stu-id="ad710-103">Native Mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for internal storage.</span></span> <span data-ttu-id="ad710-104">資料庫是必要元件，它是用來儲存已發行的報表、模型、共用資料來源、工作階段資料、資源和伺服器中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ad710-104">The database is required and it is used to store published reports, models, shared data sources, session data, resources, and server metadata.</span></span>  
  
 <span data-ttu-id="ad710-105">若要建立報表伺服器資料庫或是變更連接字串或認證，請使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員中 [資料庫] 頁面上的選項。</span><span class="sxs-lookup"><span data-stu-id="ad710-105">To create a report server database or to change the connection string or credentials, use the options in the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ad710-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式</span><span class="sxs-lookup"><span data-stu-id="ad710-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode</span></span>|  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a><span data-ttu-id="ad710-107">何時建立或設定報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="ad710-107">When to Create or Configure the Report Server Databases</span></span>  
 <span data-ttu-id="ad710-108">如果您在僅限檔案模式中安裝了報表伺服器，您就必須建立及設定報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-108">You must create and configure the report server database if you installed the report server in files-only mode.</span></span>  
  
 <span data-ttu-id="ad710-109">如果您在預設組態中安裝了原生模式的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，當安裝了報表伺服器執行個體時，就會自動建立及設定報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-109">If you installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in either the default configuration for native mode, the report server database was created and configured automatically when the report server instance was installed.</span></span> <span data-ttu-id="ad710-110">您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員來檢視或修改安裝程式為您進行的設定。</span><span class="sxs-lookup"><span data-stu-id="ad710-110">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to view or modify the settings that Setup configured for you.</span></span>  
  
##  <a name="before-you-start"></a><a name="rsdbrequirements"></a> <span data-ttu-id="ad710-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="ad710-111">Before You Start</span></span>  
 <span data-ttu-id="ad710-112">建立或設定報表伺服器資料庫是多重步驟的程序。</span><span class="sxs-lookup"><span data-stu-id="ad710-112">Creating or configuring a report server database is a multi-step process.</span></span> <span data-ttu-id="ad710-113">在您建立報表伺服器資料庫之前，請考慮您要如何指定以下項目：</span><span class="sxs-lookup"><span data-stu-id="ad710-113">Before you create the report server database, consider how you want to specify the following items:</span></span>  
  
 <span data-ttu-id="ad710-114">選取資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="ad710-114">Select a database server</span></span>  
 <span data-ttu-id="ad710-115">檢閱支援的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 版本，以及[建立報表伺服器資料庫 &#40;SSRS 組態管理員&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) 主題中受支援的版本。</span><span class="sxs-lookup"><span data-stu-id="ad710-115">Review the supported versions of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and review the supported editions in the topic, [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="ad710-116">啟用 TCP/IP 連接</span><span class="sxs-lookup"><span data-stu-id="ad710-116">Enable TCP/IP connections</span></span>  
 <span data-ttu-id="ad710-117">針對 [!INCLUDE[ssDE](../../includes/ssde-md.md)]啟用 TCP/IP 連接。</span><span class="sxs-lookup"><span data-stu-id="ad710-117">Enable TCP/IP connections for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="ad710-118">某些版本的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 依預設並不會啟用 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="ad710-118">Some editions of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] do not enable TCP/IP by default.</span></span> <span data-ttu-id="ad710-119">本主題將提供指示。</span><span class="sxs-lookup"><span data-stu-id="ad710-119">Instructions are provided in this topic.</span></span>  
  
 <span data-ttu-id="ad710-120">為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開啟通訊埠</span><span class="sxs-lookup"><span data-stu-id="ad710-120">Open port for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="ad710-121">對遠端伺服器而言，如果您正在使用防火牆軟體，您必須開啟 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 接聽的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ad710-121">For a remote server, if you are using firewall software, you must open the port that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] listens on.</span></span>  
  
 <span data-ttu-id="ad710-122">決定報表伺服器認證</span><span class="sxs-lookup"><span data-stu-id="ad710-122">Decide on report server credentials</span></span>  
 <span data-ttu-id="ad710-123">決定報表伺服器將如何連接到報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-123">Decide how the report server will connect to the report server databases.</span></span> <span data-ttu-id="ad710-124">認證類型包括網域使用者帳戶、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫使用者帳戶或報表伺服器服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad710-124">Credential types include domain user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database user account, or the Report Server service account.</span></span>  
  
 <span data-ttu-id="ad710-125">這些認證會加密並儲存於 RSReportServer.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ad710-125">These credentials are encrypted and stored in the RSReportServer.config file.</span></span> <span data-ttu-id="ad710-126">報表伺服器會將這些認證用於對報表伺服器資料庫的進行中連接。</span><span class="sxs-lookup"><span data-stu-id="ad710-126">The report server uses these credentials for ongoing connections to the report server database.</span></span> <span data-ttu-id="ad710-127">如果您想要使用 Windows 使用者帳戶或資料庫使用者帳戶，請務必指定已經存在的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad710-127">If you want to use a Windows user account or a database user account, be sure to specify one that already exists.</span></span> <span data-ttu-id="ad710-128">雖然 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員將會建立登入並設定必要的權限，但是它不會為您建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad710-128">Although the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager will create a login and set the necessary permissions, it will not create an account for you.</span></span> <span data-ttu-id="ad710-129">如需詳細資訊，請參閱[將報表伺服器資料庫連接設定 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ad710-129">For more information, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="ad710-130">決定報表伺服器語言</span><span class="sxs-lookup"><span data-stu-id="ad710-130">Decide on a report server language</span></span>  
 <span data-ttu-id="ad710-131">選擇要為報表伺服器指定的語言。</span><span class="sxs-lookup"><span data-stu-id="ad710-131">Choose a language to specify for the report server.</span></span> <span data-ttu-id="ad710-132">當使用者使用不同語言版本的瀏覽器連接到伺服器時，預先定義的角色名稱、描述和 [我的報表] 資料夾並不會以不同的語言顯示。</span><span class="sxs-lookup"><span data-stu-id="ad710-132">Predefined role names, descriptions, and the My Reports folders do not appear in different languages when users connect to the server using different language versions of a browser.</span></span>  
  
 <span data-ttu-id="ad710-133">檢查認證來建立並提供資料庫</span><span class="sxs-lookup"><span data-stu-id="ad710-133">Check credentials to create and provision the database</span></span>  
 <span data-ttu-id="ad710-134">確認您的帳戶認證有權在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-134">Verify that you have account credentials that have permission to create databases on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="ad710-135">這些認證會用於單次連接，以建立報表伺服器資料庫和 **RSExecRole**。</span><span class="sxs-lookup"><span data-stu-id="ad710-135">These credentials are used for a one-time connection to create the report server database and **RSExecRole**.</span></span> <span data-ttu-id="ad710-136">如果登入尚未存在，將會針對報表伺服器所使用的帳戶來建立資料庫使用者登入，以連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-136">If a login does not already exist, a database user login will be created for the account used by the report server to connect to the database.</span></span> <span data-ttu-id="ad710-137">您可以在登入所使用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶之下連接，或者也可以輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫登入。</span><span class="sxs-lookup"><span data-stu-id="ad710-137">You can connect under the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you are logged in as, or you can enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a><span data-ttu-id="ad710-138">啟用對遠端報表伺服器資料庫的存取</span><span class="sxs-lookup"><span data-stu-id="ad710-138">To enable access to a remote report server database</span></span>  
  
1.  <span data-ttu-id="ad710-139">如果您正在使用遠端 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，請登入資料庫伺服器，以確認或啟用 TCP/IP 連接。</span><span class="sxs-lookup"><span data-stu-id="ad710-139">If you are using a remote [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, log on to the database server to verify or enable TCP/IP connections.</span></span>  
  
2.  <span data-ttu-id="ad710-140">依序指向 **[開始]**、 **[所有程式]**、 **[Microsoft SQL Server]**、 **[組態工具]**，然後按一下 **[SQL Server 組態管理員]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-140">Point to **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="ad710-141">開啟**SQL Server 網路**設定]。</span><span class="sxs-lookup"><span data-stu-id="ad710-141">Open **SQL Server Network Configuration**.</span></span>  
  
4.  <span data-ttu-id="ad710-142">選取執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad710-142">Select the instance.</span></span>  
  
5.  <span data-ttu-id="ad710-143">以滑鼠右鍵按一下 **[TCP/IP]** ，然後按一下 **[已啟用]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-143">Right-click **TCP/IP** and click **Enabled**.</span></span>  
  
6.  <span data-ttu-id="ad710-144">重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="ad710-144">Restart the service.</span></span>  
  
7.  <span data-ttu-id="ad710-145">開啟防火牆軟體，並開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ad710-145">Open your firewall software and open the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on.</span></span> <span data-ttu-id="ad710-146">如果是預設執行個體，這對於 TCP/IP 連接通常是通訊埠 1433。</span><span class="sxs-lookup"><span data-stu-id="ad710-146">For the default instance, this is typically port 1433 for TCP/IP connections.</span></span> <span data-ttu-id="ad710-147">如需詳細資訊，請參閱《 [線上叢書》的](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 設定用於 Database Engine 存取的 Windows 防火牆 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-147">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
### <a name="to-create-a-local-report-server-database"></a><span data-ttu-id="ad710-148">若要建立本機報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="ad710-148">To create a local report server database</span></span>  
  
1.  <span data-ttu-id="ad710-149">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並連接到您正在建立資料庫的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad710-149">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and connect to the report server instance for which you are creating the database.</span></span> <span data-ttu-id="ad710-150">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="ad710-150">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="ad710-151">在 [資料庫] 頁面上，按一下 **[變更資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-151">On the Database page, click **Change Database**.</span></span>  
  
3.  <span data-ttu-id="ad710-152">按一下 **[建立新的報表伺服器資料庫]**，再按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-152">Click **Create a new report server database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ad710-153">連接到將用來建立及主控報表伺服器資料庫的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體：</span><span class="sxs-lookup"><span data-stu-id="ad710-153">Connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that you will use to create and host the report server database:</span></span>  
  
    1.  <span data-ttu-id="ad710-154">輸入您想要使用的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad710-154">Type the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that you want to use.</span></span> <span data-ttu-id="ad710-155">此精靈將會顯示本機 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，它會當做預設執行個體 (如果有的話) 來執行。</span><span class="sxs-lookup"><span data-stu-id="ad710-155">The wizard will display a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs as the default instance if it is available.</span></span> <span data-ttu-id="ad710-156">否則，您必須輸入要使用的伺服器和執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad710-156">Otherwise, you must type the server and instance to use.</span></span> <span data-ttu-id="ad710-157">命名實例是以下列格式指定： \<servername> \\<instancename \> 。</span><span class="sxs-lookup"><span data-stu-id="ad710-157">Named instances are specified in this format: \<servername>\\<instancename\>.</span></span>  
  
    2.  <span data-ttu-id="ad710-158">輸入用於與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 之單次連接的認證，以便建立報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-158">Enter the credentials used for a one-time connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the purpose of creating the report server databases.</span></span> <span data-ttu-id="ad710-159">如需有關如何使用這些認證的詳細資訊，請參閱本主題的「 [在開始之前](#rsdbrequirements) 」。</span><span class="sxs-lookup"><span data-stu-id="ad710-159">For more information about how these credentials are used, see [Before You Start](#rsdbrequirements) in this topic.</span></span>  
  
    3.  <span data-ttu-id="ad710-160">按一下 **[測試連接]** 可驗證與伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="ad710-160">Click **Test Connection** to validate the connection to the server.</span></span>  
  
    4.  <span data-ttu-id="ad710-161">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-161">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="ad710-162">指定用來建立資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad710-162">Specify properties used to create the database.</span></span> <span data-ttu-id="ad710-163">如需有關如何使用這些屬性的詳細資訊，請參閱本主題的「 [在開始之前](#rsdbrequirements) 」。</span><span class="sxs-lookup"><span data-stu-id="ad710-163">For more information about how these properties are used, see [Before You Start](#rsdbrequirements) in this topic:</span></span>  
  
    1.  <span data-ttu-id="ad710-164">輸入報表伺服器資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad710-164">Type the name of the report server database.</span></span> <span data-ttu-id="ad710-165">會伴隨主要資料庫，建立一個暫存資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad710-165">A temporary database is created along with the primary database.</span></span> <span data-ttu-id="ad710-166">請考慮使用描述性名稱來協助您記住資料庫的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ad710-166">Consider using a descriptive name to help you remember how the database is used.</span></span> <span data-ttu-id="ad710-167">請注意，您所指定的名稱將會在資料庫的存留期間使用。</span><span class="sxs-lookup"><span data-stu-id="ad710-167">Note that the name you specify will be used for the lifetime of the database.</span></span> <span data-ttu-id="ad710-168">當您建立報表伺服器資料庫之後，就無法重新命名了。</span><span class="sxs-lookup"><span data-stu-id="ad710-168">You cannot rename a report server database after it is created.</span></span>  
  
    2.  <span data-ttu-id="ad710-169">選取您希望角色定義和 [我的報表] 所顯示的語言。</span><span class="sxs-lookup"><span data-stu-id="ad710-169">Select the language in which you want role definitions and My Reports to appear.</span></span>  
  
    3.  <span data-ttu-id="ad710-170">報表伺服器模式一律設定為 **[原生]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-170">The Report Server Mode is always set to **Native**.</span></span>  
  
    4.  <span data-ttu-id="ad710-171">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-171">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="ad710-172">指定報表伺服器用來連接到報表伺服器資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="ad710-172">Specify the credentials used by the report server to connect to the report server database.</span></span>  
  
    1.  <span data-ttu-id="ad710-173">指定驗證類型：</span><span class="sxs-lookup"><span data-stu-id="ad710-173">Specify the authentication type:</span></span>  
  
         <span data-ttu-id="ad710-174">使用已經定義的 **資料庫登入，選取要連接的** [資料庫認證] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-174">Select **Database Credentials** to connect using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login that is already defined.</span></span> <span data-ttu-id="ad710-175">如果報表伺服器位於不同網域、非信任網域或防火牆後面的電腦上，則建議使用資料庫認證。</span><span class="sxs-lookup"><span data-stu-id="ad710-175">Using database credentials is recommended if the report server is on a computer that is in a different domain, a non-trusted domain, or behind a firewall.</span></span>  
  
         <span data-ttu-id="ad710-176">如果您具有最低權限的網域使用者帳戶，而該帳戶具有登入電腦和資料庫伺服器的權限，請選取 **[Windows 認證]** 。</span><span class="sxs-lookup"><span data-stu-id="ad710-176">Select **Windows Credentials** if you have a least-privileged domain user account that has permission to log on to the computer and the database server.</span></span>  
  
         <span data-ttu-id="ad710-177">如果您希望報表伺服器使用它的服務帳戶進行連接，請選取 **[服務認證]** 。</span><span class="sxs-lookup"><span data-stu-id="ad710-177">Select **Service Credentials** if you want the report server to connect using its service account.</span></span> <span data-ttu-id="ad710-178">有了這個選項，伺服器就會使用整合式安全性來進行連接；認證並不會加密或儲存起來。</span><span class="sxs-lookup"><span data-stu-id="ad710-178">With this option, the server connects using integrated security; credentials are not encrypted or stored.</span></span>  
  
    2.  <span data-ttu-id="ad710-179">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-179">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="ad710-180">檢閱 [摘要] 頁面上的資訊，以確認設定都正確無誤，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad710-180">Review the information on the Summary page to verify the settings are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="ad710-181">按一下報表伺服器 URL 頁面或報表管理員 URL 頁面上的 URL 來確認連接。</span><span class="sxs-lookup"><span data-stu-id="ad710-181">Verify the connection by clicking a URL on the Report Server URL page or Report Manager URL page.</span></span> <span data-ttu-id="ad710-182">必須有定義 URL，這項測試才有效。</span><span class="sxs-lookup"><span data-stu-id="ad710-182">The URLs must be defined in order for this test to work.</span></span> <span data-ttu-id="ad710-183">如果報表伺服器資料庫連接有效，您將會在瀏覽器視窗中看到報表伺服器資料夾階層或報表管理員。</span><span class="sxs-lookup"><span data-stu-id="ad710-183">If the report server database connection is valid, you will see either the report server folder hierarchy or Report Manager in a browser window.</span></span> <span data-ttu-id="ad710-184">如需詳細資訊，請參閱《 [線上叢書》的](verify-a-reporting-services-installation.md) 驗證 Reporting Services 安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad710-184">For more information, see [Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad710-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad710-185">See Also</span></span>  
 <span data-ttu-id="ad710-186">[&#40;SSRS Configuration Manager 設定報表伺服器資料庫連接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ad710-186">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="ad710-187">[資料庫 &#40;SSRS 原生模式&#41;](../../sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ad710-187">[Database &#40;SSRS Native Mode&#41;](../../sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="ad710-188">[管理 Reporting Services 的原生模式報表伺服器](../report-server/manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad710-188">[Manage a Reporting Services Native Mode Report Server](../report-server/manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="ad710-189">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="ad710-189">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
