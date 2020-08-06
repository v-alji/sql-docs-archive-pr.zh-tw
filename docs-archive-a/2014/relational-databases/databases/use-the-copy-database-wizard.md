---
title: 使用複製資料庫精靈 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0baaeef6cb196a67b2f615aa280b61b61fbc5119
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708442"
---
# <a name="use-the-copy-database-wizard"></a><span data-ttu-id="556ba-102">使用複製資料庫精靈</span><span class="sxs-lookup"><span data-stu-id="556ba-102">Use the Copy Database Wizard</span></span>
  <span data-ttu-id="556ba-103">「複製資料庫精靈」可讓您輕鬆地在伺服器之間移動或複製資料庫及其物件，而不需要讓伺服器停機。</span><span class="sxs-lookup"><span data-stu-id="556ba-103">The Copy Database Wizard lets you move or copy databases and their objects easily from one server to another, with no server downtime.</span></span> <span data-ttu-id="556ba-104">您也可以將資料庫從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="556ba-104">You can also upgrade databases from a previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="556ba-105">使用此精靈可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="556ba-105">By using this wizard, you can do the following:</span></span>  
  
-   <span data-ttu-id="556ba-106">挑選來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-106">Pick a source and destination server.</span></span>  
  
-   <span data-ttu-id="556ba-107">選取要移動、複製或升級的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-107">Select databases to move, copy or upgrade.</span></span>  
  
-   <span data-ttu-id="556ba-108">為資料庫指定檔案位置。</span><span class="sxs-lookup"><span data-stu-id="556ba-108">Specify the file location for the databases.</span></span>  
  
-   <span data-ttu-id="556ba-109">在目的地伺服器上建立登入。</span><span class="sxs-lookup"><span data-stu-id="556ba-109">Create logins on the destination server.</span></span>  
  
-   <span data-ttu-id="556ba-110">複製其他支援的物件、作業、使用者定義的預存程序和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="556ba-110">Copy additional supporting objects, jobs, user-defined stored procedures, and error messages.</span></span>  
  
-   <span data-ttu-id="556ba-111">何時要移動或複製資料庫的排程。</span><span class="sxs-lookup"><span data-stu-id="556ba-111">Schedule when to move or copy the databases.</span></span>  
  
 <span data-ttu-id="556ba-112">除了複製資料庫以外，您還可以複製相關的中繼資料，例如，被複製之資料庫所需之 **master** 資料庫中的登入和物件。</span><span class="sxs-lookup"><span data-stu-id="556ba-112">In addition to copying databases, you can copy associated metadata, for example, logins and objects from the **master** database that are required by a copied database.</span></span>  
  
 <span data-ttu-id="556ba-113">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="556ba-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="556ba-114">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="556ba-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="556ba-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="556ba-115">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="556ba-116">先決條件</span><span class="sxs-lookup"><span data-stu-id="556ba-116">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="556ba-117">建議</span><span class="sxs-lookup"><span data-stu-id="556ba-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="556ba-118">安全性</span><span class="sxs-lookup"><span data-stu-id="556ba-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="556ba-119">**將複製資料庫精靈用於：**</span><span class="sxs-lookup"><span data-stu-id="556ba-119">**Using the Copy Database Wizard to:**</span></span>  
  
     [<span data-ttu-id="556ba-120">複製、移動或升級資料庫</span><span class="sxs-lookup"><span data-stu-id="556ba-120">Copy, Move, or Upgrade Databases</span></span>](#Copy_Move)  
  
-   <span data-ttu-id="556ba-121">**待處理，升級之後：**</span><span class="sxs-lookup"><span data-stu-id="556ba-121">**Follow up, after upgrade:**</span></span>  
  
     [<span data-ttu-id="556ba-122">升級 SQL Server 資料庫之後</span><span class="sxs-lookup"><span data-stu-id="556ba-122">After Upgrading a SQL Server Database</span></span>](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="556ba-123">開始之前</span><span class="sxs-lookup"><span data-stu-id="556ba-123">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="556ba-124">限制事項</span><span class="sxs-lookup"><span data-stu-id="556ba-124">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="556ba-125">Express 版本不提供複製資料庫精靈。</span><span class="sxs-lookup"><span data-stu-id="556ba-125">The Copy Database Wizard is not available in the Express edition.</span></span>  
  
-   <span data-ttu-id="556ba-126">複製資料庫精靈無法用於複製或移動下列資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-126">The Copy Database Wizard cannot be used to copy or move the following databases.</span></span>  
  
    -   <span data-ttu-id="556ba-127">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="556ba-127">System databases</span></span>  
  
    -   <span data-ttu-id="556ba-128">要用於複寫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-128">Databases marked for replication.</span></span>  
  
    -   <span data-ttu-id="556ba-129">標示為「無法存取」、「正在載入」、「離線」、「正在復原」、「有疑問」或是「緊急模式」的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-129">Databases marked Inaccessible, Loading, Offline, Recovering, Suspect, or in Emergency Mode.</span></span>  
  
-   <span data-ttu-id="556ba-130">資料庫升級後，無法降級至舊版。</span><span class="sxs-lookup"><span data-stu-id="556ba-130">After a database has been upgraded, it cannot be downgraded to a previous version.</span></span>  
  
-   <span data-ttu-id="556ba-131">若您選取 **[移動]** 選項，則當移動資料庫之後，精靈會自動刪除來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-131">If you select the **Move** option, the wizard deletes the source database automatically after moving the database.</span></span> <span data-ttu-id="556ba-132">如果您選取 **[複製]** 選項，「複製資料庫精靈」就不會刪除來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-132">The Copy Database Wizard does not delete a source database if you select the **Copy** option.</span></span>  
  
-   <span data-ttu-id="556ba-133">如果您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件方法來移動全文檢索目錄，您必須在移動之後重新擴展索引。</span><span class="sxs-lookup"><span data-stu-id="556ba-133">If you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method to move the full-text catalog, you must repopulate the index after the move.</span></span>  
  
-   <span data-ttu-id="556ba-134">卸離和附加方法可卸離資料庫、移動或複製資料庫 .mdf、.ndf 和 .ldf 檔案，並在新的位置中重新附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-134">The detach-and-attach method detaches the database, moves or copies the database .mdf, .ndf, .ldf files and reattaches the database in the new location.</span></span> <span data-ttu-id="556ba-135">對於卸離和附加方法而言，為了避免資料遺失或不一致，使用中工作階段不能附加到正在移動或複製的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-135">For the detach-and-attach method, to avoid data loss or inconsistency, active sessions cannot be attached to the database being moved or copied.</span></span> <span data-ttu-id="556ba-136">如果有任何使用中工作階段存在，「複製資料庫精靈」將不會執行移動或複製作業。</span><span class="sxs-lookup"><span data-stu-id="556ba-136">If any active sessions exist, the Copy Database Wizard does not execute the move or copy operation.</span></span> <span data-ttu-id="556ba-137">對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件方法而言，因為資料庫絕對不會離線，所以允許使用中工作階段。</span><span class="sxs-lookup"><span data-stu-id="556ba-137">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method, active sessions are allowed because the database is never taken offline.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="556ba-138">必要條件</span><span class="sxs-lookup"><span data-stu-id="556ba-138">Prerequisites</span></span>  
 <span data-ttu-id="556ba-139">確定目的地伺服器上已啟動 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="556ba-139">Ensure that SQL Server Agent is started on the destination server.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="556ba-140">建議</span><span class="sxs-lookup"><span data-stu-id="556ba-140">Recommendations</span></span>  
  
-   <span data-ttu-id="556ba-141">為了確保升級的資料庫能有最佳效能，請針對升級的資料庫執行 sp_updatestats (更新統計資料)。</span><span class="sxs-lookup"><span data-stu-id="556ba-141">To ensure optimal performance of an upgraded database, run sp_updatestats (update statistics) against the upgraded database.</span></span>  
  
-   <span data-ttu-id="556ba-142">將資料庫複製到另一個伺服器執行個體時，為了提供一致的經驗給使用者和應用程式，您可能會需要在其他伺服器執行個體上為資料庫重新建立部分或所有中繼資料，例如登入和作業。</span><span class="sxs-lookup"><span data-stu-id="556ba-142">When you copy a database to another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="556ba-143">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="556ba-143">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="556ba-144">Security</span><span class="sxs-lookup"><span data-stu-id="556ba-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="556ba-145">權限</span><span class="sxs-lookup"><span data-stu-id="556ba-145">Permissions</span></span>  
 <span data-ttu-id="556ba-146">您必須在來源伺服器與目的地伺服器上成為 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="556ba-146">You must be a member of the **sysadmin** fixed server role on both the source and destination servers.</span></span>  
  
##  <a name="copy-move-or-upgrade-databases"></a><a name="Copy_Move"></a><span data-ttu-id="556ba-147">複製、移動或升級資料庫</span><span class="sxs-lookup"><span data-stu-id="556ba-147">Copy, Move or Upgrade Databases</span></span>  
  
1.  <span data-ttu-id="556ba-148">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [物件總管] 中，展開 **[資料庫]**，然後以滑鼠右鍵按一下資料庫，再指向 **[工作]**，然後按一下 **[複製資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="556ba-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Copy Database**.</span></span>  
  
2.  <span data-ttu-id="556ba-149">從 **[選取來源伺服器]** 頁面，指定要移動或複製之資料庫所在的伺服器，以及輸入登入資訊。</span><span class="sxs-lookup"><span data-stu-id="556ba-149">From the **Select a Source Server** page, specify the server with the database to move or copy, and to enter login information.</span></span> <span data-ttu-id="556ba-150">在您選取驗證方法並輸入登入資訊之後，按 **[下一步]** 以建立與來源伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="556ba-150">After you select the authentication method and enter login information, click **Next** to establish the connection to the source server.</span></span> <span data-ttu-id="556ba-151">在整個工作階段中，此連接會保持開啟。</span><span class="sxs-lookup"><span data-stu-id="556ba-151">This connection remains open throughout the session.</span></span>  
  
     <span data-ttu-id="556ba-152">**來源伺服器**</span><span class="sxs-lookup"><span data-stu-id="556ba-152">**Source server**</span></span>  
     <span data-ttu-id="556ba-153">選取您想要移動或複製之資料庫所在的伺服器名稱，或是按一下瀏覽 (**...**) 按鈕，尋找您要的伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-153">Select the name of the server on which the database or databases you want to move or copy are located, or click the browse (**...**) button to locate the server you want.</span></span> <span data-ttu-id="556ba-154">該伺服器必須至少為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="556ba-154">The server must be at least [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="556ba-155">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="556ba-155">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="556ba-156">可讓使用者透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="556ba-156">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="556ba-157">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="556ba-157">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="556ba-158">可讓使用者經由提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證使用者名稱和密碼來進行連接。</span><span class="sxs-lookup"><span data-stu-id="556ba-158">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="556ba-159">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="556ba-159">**User name**</span></span>  
     <span data-ttu-id="556ba-160">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-160">Enter the user name to connect with.</span></span> <span data-ttu-id="556ba-161">這個選項只有在您選取了使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時才可以使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-161">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication .</span></span>  
  
     <span data-ttu-id="556ba-162">**密碼**</span><span class="sxs-lookup"><span data-stu-id="556ba-162">**Password**</span></span>  
     <span data-ttu-id="556ba-163">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="556ba-163">Enter the password for the login.</span></span> <span data-ttu-id="556ba-164">這個選項只有在您選取了使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時才可以使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-164">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="556ba-165">**下一個**</span><span class="sxs-lookup"><span data-stu-id="556ba-165">**Next**</span></span>  
     <span data-ttu-id="556ba-166">連接到伺服器，並驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="556ba-166">Connect to the server and validate the user.</span></span> <span data-ttu-id="556ba-167">此處理序會檢查使用者是否為所選取電腦中的 **[系統管理員 (sysadmin)]** 固定伺服器角色成員。</span><span class="sxs-lookup"><span data-stu-id="556ba-167">This process checks whether the user is a member of the **sysadmin** fixed server role on the selected computer.</span></span>  
  
3.  <span data-ttu-id="556ba-168">從 **[選取目的地伺服器]** 頁面，指定將移動或複製資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-168">From the **Select a Destination Server** page, specify the server where the database will be moved or copied.</span></span> <span data-ttu-id="556ba-169">如果您將來源和目的地伺服器設定成同一個伺服器執行個體，您就會複製一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-169">If you set the source and destination servers to the same server instance, you will make a copy of a database.</span></span> <span data-ttu-id="556ba-170">在這種情況下，您必須稍後在精靈中重新命名此資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-170">In this case you must rename the database at a later point in the wizard.</span></span> <span data-ttu-id="556ba-171">只有當目的地伺服器上沒有名稱衝突時，才可以將來源資料庫名稱用於複製或移動的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-171">The source database name can be used for the copied or moved database only if name conflicts do not exist on the destination server.</span></span> <span data-ttu-id="556ba-172">如果有名稱衝突存在，您必須先手動解決目的地伺服器上的衝突，然後才能在這裡使用來源資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-172">If name conflicts exist, you must resolve them manually on the destination server before you can use the source database name there.</span></span>  
  
     <span data-ttu-id="556ba-173">**目的地伺服器**</span><span class="sxs-lookup"><span data-stu-id="556ba-173">**Destination server**</span></span>  
     <span data-ttu-id="556ba-174">選取要移動或複製資料庫的目的地伺服器名稱，或按一下瀏覽 (**...**) 按鈕來尋找目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-174">Select the name of the server to which the database or databases will be moved or copied, or click the browse (**...**) button to locate a destination server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="556ba-175">您可以使用屬於叢集伺服器的目的地。「複製資料庫精靈」將會確保您只能選取叢集目的地伺服器上的共用磁碟機。</span><span class="sxs-lookup"><span data-stu-id="556ba-175">You can use a destination that is a clustered server; the Copy Database Wizard will make sure you select only shared drives on a clustered destination server.</span></span>  
  
     <span data-ttu-id="556ba-176">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="556ba-176">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="556ba-177">可讓使用者透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="556ba-177">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="556ba-178">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="556ba-178">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="556ba-179">可讓使用者經由提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證使用者名稱和密碼來進行連接。</span><span class="sxs-lookup"><span data-stu-id="556ba-179">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="556ba-180">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="556ba-180">**User name**</span></span>  
     <span data-ttu-id="556ba-181">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-181">Enter the user name to connect with.</span></span> <span data-ttu-id="556ba-182">唯有在您選取了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證之後，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-182">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="556ba-183">**密碼**</span><span class="sxs-lookup"><span data-stu-id="556ba-183">**Password**</span></span>  
     <span data-ttu-id="556ba-184">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="556ba-184">Enter the password for the login.</span></span> <span data-ttu-id="556ba-185">唯有在您選取了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證之後，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-185">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="556ba-186">**下一個**</span><span class="sxs-lookup"><span data-stu-id="556ba-186">**Next**</span></span>  
     <span data-ttu-id="556ba-187">連接到伺服器，並驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="556ba-187">Connect to the server and validate the user.</span></span> <span data-ttu-id="556ba-188">此處理序會檢查使用者在選取的電腦上是否擁有以上所列的權限。</span><span class="sxs-lookup"><span data-stu-id="556ba-188">This process checks whether the user has the permissions listed above on the selected computers.</span></span>  
  
4.  <span data-ttu-id="556ba-189">從 **[選取傳送方法]** 頁面，選取傳送方法。</span><span class="sxs-lookup"><span data-stu-id="556ba-189">From the **Select a Transfer Method** page, select the transfer method.</span></span>  
  
     <span data-ttu-id="556ba-190">**使用卸離和附加方法**</span><span class="sxs-lookup"><span data-stu-id="556ba-190">**Use the detach and attach method**</span></span>  
     <span data-ttu-id="556ba-191">從來源伺服器卸離資料庫，將資料庫檔案 (.mdf、.ndf 以及 .ldf) 複製到目的地伺服器，然後在目的地伺服器端附加該資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-191">Detach the database from the source server, copy the database files (.mdf, .ndf, and .ldf) to the destination server, and attach the database at the destination server.</span></span> <span data-ttu-id="556ba-192">此方法通常是比較快速的方法，因為它的主要工作是讀取來源磁碟和寫入目的地磁碟。</span><span class="sxs-lookup"><span data-stu-id="556ba-192">This method is usually the faster method because the principal work is reading the source disk and writing the destination disk.</span></span> <span data-ttu-id="556ba-193">不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 邏輯在資料庫中建立物件，或建立資料儲存結構。</span><span class="sxs-lookup"><span data-stu-id="556ba-193">No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logic is required to create objects within the database, or create data storage structures.</span></span> <span data-ttu-id="556ba-194">不過，如果資料庫包含大量已配置但未使用的空間，此方法就會比較慢。</span><span class="sxs-lookup"><span data-stu-id="556ba-194">This method can be slower, however, if the database contains a large amount of allocated but unused space.</span></span> <span data-ttu-id="556ba-195">例如，新的且實際上幾乎是空的資料庫，在建立時若配置 100 MB，即使資料只填滿 5 MB，也會複製全部 100 MB。</span><span class="sxs-lookup"><span data-stu-id="556ba-195">For instance, a new and practically empty database that is created allocating 100 MB, copies the entire 100 MB, even if only 5 MB is full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="556ba-196">此方法讓使用者在傳送期間無法使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-196">This method makes the database unavailable to users during the transfer.</span></span>  
  
     <span data-ttu-id="556ba-197">**如果失敗，則重新附加來源資料庫**</span><span class="sxs-lookup"><span data-stu-id="556ba-197">**If a failure occurs, reattach the source database**</span></span>  
     <span data-ttu-id="556ba-198">複製資料庫時，一律會將原始資料庫檔案重新附加至來源伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-198">When a database is copied, the original database files are always reattached to the source server.</span></span> <span data-ttu-id="556ba-199">無法完成資料庫移動時，使用這個方塊即可將原始檔案重新附加至來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-199">Use this box to reattach original files to the source database if a database move cannot be completed.</span></span>  
  
     <span data-ttu-id="556ba-200">**使用 SQL 管理物件方法**</span><span class="sxs-lookup"><span data-stu-id="556ba-200">**Use the SQL Management Object method**</span></span>  
     <span data-ttu-id="556ba-201">這個方法會讀取來源資料庫上的每個資料庫物件的定義，然後在目的地資料庫中建立每個物件。</span><span class="sxs-lookup"><span data-stu-id="556ba-201">This method reads the definition of each database object on the source database and creates each object in the destination database.</span></span> <span data-ttu-id="556ba-202">接著它會從來源資料表傳送資料到目的地資料表，重新建立索引與中繼資料。</span><span class="sxs-lookup"><span data-stu-id="556ba-202">Then it transfers the data from the source tables to the destination tables, recreating indexes and metadata.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="556ba-203">在傳送期間，資料庫使用者可以繼續存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-203">Database users can continue to access the database during the transfer.</span></span>  
  
5.  <span data-ttu-id="556ba-204">從 **[選取資料庫]** 頁面，選取您要從來源伺服器，移動或複製到目的地伺服器的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-204">From the **Select Database** page, select the database or databases you want to move or copy from the source server to the destination server.</span></span> <span data-ttu-id="556ba-205">請參閱本主題中的「開始之前」一節中的[限制和限制](#Restrictions)。</span><span class="sxs-lookup"><span data-stu-id="556ba-205">See [Limitations and Restrictions](#Restrictions) in the 'Before You Begin' section of this topic.</span></span>  
  
     <span data-ttu-id="556ba-206">**移動**</span><span class="sxs-lookup"><span data-stu-id="556ba-206">**Move**</span></span>  
     <span data-ttu-id="556ba-207">移動資料庫至目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-207">Move the database to the destination server.</span></span>  
  
     <span data-ttu-id="556ba-208">**複製**</span><span class="sxs-lookup"><span data-stu-id="556ba-208">**Copy**</span></span>  
     <span data-ttu-id="556ba-209">複製資料庫至目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="556ba-209">Copy the database to the destination server.</span></span>  
  
     <span data-ttu-id="556ba-210">**Source**</span><span class="sxs-lookup"><span data-stu-id="556ba-210">**Source**</span></span>  
     <span data-ttu-id="556ba-211">顯示存在於來源伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-211">Displays the databases that exist on the source server.</span></span>  
  
     <span data-ttu-id="556ba-212">**狀態**</span><span class="sxs-lookup"><span data-stu-id="556ba-212">**Status**</span></span>  
     <span data-ttu-id="556ba-213">如果可以移動資料庫，就會顯示 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="556ba-213">Displays **OK** if the database can be moved.</span></span> <span data-ttu-id="556ba-214">否則就會顯示無法移動資料庫的原因。</span><span class="sxs-lookup"><span data-stu-id="556ba-214">Otherwise displays the reason why the database cannot be moved.</span></span>  
  
     <span data-ttu-id="556ba-215">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="556ba-215">**Refresh**</span></span>  
     <span data-ttu-id="556ba-216">重新整理資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="556ba-216">Refresh the list of databases.</span></span>  
  
     <span data-ttu-id="556ba-217">**下一個**</span><span class="sxs-lookup"><span data-stu-id="556ba-217">**Next**</span></span>  
     <span data-ttu-id="556ba-218">開始驗證處理，然後移動到下一個畫面。</span><span class="sxs-lookup"><span data-stu-id="556ba-218">Start the validation process, and then move to the next screen.</span></span>  
  
6.  <span data-ttu-id="556ba-219">從 **[設定目的地資料庫]** 頁面，適當地變更資料庫名稱，以及指定資料庫檔案的位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-219">From the **Configure Destination Database** page, change the database name if appropriate and specify the location and names of the database files.</span></span> <span data-ttu-id="556ba-220">每次移動或複製各個資料庫時，就會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="556ba-220">This page appears once for each database being moved or copied.</span></span>  
  
7.  <span data-ttu-id="556ba-221">從 **[選取資料庫物件]** 頁面，選取要包含在移動或複製作業中的物件。</span><span class="sxs-lookup"><span data-stu-id="556ba-221">From the **Select Database Objects** page, select the objects to include in the move or copy operation.</span></span> <span data-ttu-id="556ba-222">此頁面只能在來源和目的地是不同的伺服器時使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-222">This page is only available when the source and destination are different servers.</span></span> <span data-ttu-id="556ba-223">若要包含物件，請按一下 [可用的相關物件]\*\*\*\* 方塊中的物件名稱，然後按一下 [>>]\*\*\*\* 按鈕，將物件移至 [選取的相關物件]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="556ba-223">To include an object, click the object name in the **Available related objects** box, and then click the **>>** button to move the object to the **Selected related objects** box.</span></span> <span data-ttu-id="556ba-224">若要排除物件，請按一下 [**選取的相關物件**] 方塊中的物件名稱，然後按一下按鈕，將 **<\<** 物件移至 [**可用的相關物件**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="556ba-224">To exclude an object, click the object name in the **Selected related objects** box, and then click the **<\<** button to move the object to the **Available related objects** box.</span></span> <span data-ttu-id="556ba-225">根據預設，屬於所選取類型的所有物件都會傳送。</span><span class="sxs-lookup"><span data-stu-id="556ba-225">By default all objects of each selected type are transferred.</span></span> <span data-ttu-id="556ba-226">若要選擇任何類型的個別物件，請按一下 **[選取的相關物件]** 方塊中之任何物件類型旁的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="556ba-226">To choose individual objects of any type, click the ellipsis button next to any object type in the **Selected related objects** box.</span></span> <span data-ttu-id="556ba-227">這會開啟一個對話方塊，其中您可以選取個別物件。</span><span class="sxs-lookup"><span data-stu-id="556ba-227">This opens a dialog box where you can select individual objects.</span></span>  
  
     <span data-ttu-id="556ba-228">**登入 (執行階段的所有登入)**</span><span class="sxs-lookup"><span data-stu-id="556ba-228">**Logins (All logins at run time)**</span></span>  
     <span data-ttu-id="556ba-229">在移動或複製作業中加入登入。</span><span class="sxs-lookup"><span data-stu-id="556ba-229">Include logins in the move or copy operation.</span></span> <span data-ttu-id="556ba-230">依預設為已選取。</span><span class="sxs-lookup"><span data-stu-id="556ba-230">Selected by default.</span></span>  
  
     <span data-ttu-id="556ba-231">**master 資料庫裡的預存程序**</span><span class="sxs-lookup"><span data-stu-id="556ba-231">**Stored procedures from master database**</span></span>  
     <span data-ttu-id="556ba-232">將 **master** 資料庫裡的預存程序包含在移動或複製作業中。</span><span class="sxs-lookup"><span data-stu-id="556ba-232">Include stored procedures from the **master** database in the move or copy operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="556ba-233">擴充預存程序及其相關聯的 DLL 不適合自動複製。</span><span class="sxs-lookup"><span data-stu-id="556ba-233">Extended stored procedures and their associated DLLs are not eligible for automated copy.</span></span>  
  
     <span data-ttu-id="556ba-234">**SQL Server Agent 作業**</span><span class="sxs-lookup"><span data-stu-id="556ba-234">**SQL Server Agent jobs**</span></span>  
     <span data-ttu-id="556ba-235">將 **msdb** 資料庫裡的作業包含在移動或複製作業中。</span><span class="sxs-lookup"><span data-stu-id="556ba-235">Include jobs from the **msdb** database in the move or copy operation.</span></span>  
  
     <span data-ttu-id="556ba-236">**使用者自訂錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="556ba-236">**User-defined error messages**</span></span>  
     <span data-ttu-id="556ba-237">將使用者自訂錯誤訊息包含在移動或複製作業中。</span><span class="sxs-lookup"><span data-stu-id="556ba-237">Include user-defined error messages in the move or copy operation.</span></span>  
  
     <span data-ttu-id="556ba-238">**端點**</span><span class="sxs-lookup"><span data-stu-id="556ba-238">**Endpoints**</span></span>  
     <span data-ttu-id="556ba-239">包含在來源資料庫中所定義的端點。</span><span class="sxs-lookup"><span data-stu-id="556ba-239">Include endpoints defined in the source database.</span></span>  
  
     <span data-ttu-id="556ba-240">**全文檢索目錄**</span><span class="sxs-lookup"><span data-stu-id="556ba-240">**Full-text catalog**</span></span>  
     <span data-ttu-id="556ba-241">包含來源資料庫中的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="556ba-241">Include full-text catalogs from the source database.</span></span>  
  
     <span data-ttu-id="556ba-242">**SSIS 封裝**</span><span class="sxs-lookup"><span data-stu-id="556ba-242">**SSIS Package**</span></span>  
     <span data-ttu-id="556ba-243">包含在來源資料庫中所定義的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="556ba-243">Include [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages defined in the source database.</span></span>  
  
     <span data-ttu-id="556ba-244">**說明**</span><span class="sxs-lookup"><span data-stu-id="556ba-244">**Description**</span></span>  
     <span data-ttu-id="556ba-245">對物件的描述。</span><span class="sxs-lookup"><span data-stu-id="556ba-245">A description of the object.</span></span>  
  
8.  <span data-ttu-id="556ba-246">從 **[來源資料庫檔案的位置]** 頁面，指定包含來源伺服器資料庫檔案的檔案系統共用。</span><span class="sxs-lookup"><span data-stu-id="556ba-246">From the **Location of Source Database Files** page, specify a file system share that contains the database files on the source server.</span></span> <span data-ttu-id="556ba-247">如果來源和目的地伺服器執行個體位於不同的電腦上，這就是必要項。</span><span class="sxs-lookup"><span data-stu-id="556ba-247">This is required if the source and destination server instances are on different computers.</span></span>  
  
     <span data-ttu-id="556ba-248">**Database**</span><span class="sxs-lookup"><span data-stu-id="556ba-248">**Database**</span></span>  
     <span data-ttu-id="556ba-249">顯示要移動的每個資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-249">Displays the name of each database being moved.</span></span>  
  
     <span data-ttu-id="556ba-250">**資料夾位置**</span><span class="sxs-lookup"><span data-stu-id="556ba-250">**Folder location**</span></span>  
     <span data-ttu-id="556ba-251">指定檔案系統上之來源資料庫檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="556ba-251">Specify the location of the source database files on the file system.</span></span>  
  
     <span data-ttu-id="556ba-252">例如：C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span><span class="sxs-lookup"><span data-stu-id="556ba-252">For example: C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span></span>  
  
     <span data-ttu-id="556ba-253">**來源伺服器上的檔案共用**</span><span class="sxs-lookup"><span data-stu-id="556ba-253">**File share on source server**</span></span>  
     <span data-ttu-id="556ba-254">將來源資料庫檔案的位置指定為檔案共用的路徑。</span><span class="sxs-lookup"><span data-stu-id="556ba-254">Specify the location of the source database files as a path of a file share.</span></span>  
  
     <span data-ttu-id="556ba-255">例如： " \\ \\ *server_name*\c $ \Program Files\Microsoft SQL Server\MSSQL110。MSSQLSERVER\MSSQL\Data</span><span class="sxs-lookup"><span data-stu-id="556ba-255">For example: "\\\\*server_name*\C$\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\Data</span></span>  
  
9. <span data-ttu-id="556ba-256">複製資料庫精靈會建立 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝來傳送資料庫。請從 **[設定封裝]** 頁面適當地自訂封裝。</span><span class="sxs-lookup"><span data-stu-id="556ba-256">The Copy Database Wizard creates a [!INCLUDE[ssIS](../../includes/ssis-md.md)] package to transfer the database From the **Configure the Package** page, customize the package if appropriate.</span></span>  
  
     <span data-ttu-id="556ba-257">**封裝位置**</span><span class="sxs-lookup"><span data-stu-id="556ba-257">**Package location**</span></span>  
     <span data-ttu-id="556ba-258">顯示 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的寫入位置。</span><span class="sxs-lookup"><span data-stu-id="556ba-258">Displays where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package will be written.</span></span>  
  
     <span data-ttu-id="556ba-259">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="556ba-259">**Package name**</span></span>  
     <span data-ttu-id="556ba-260">輸入 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="556ba-260">Enter a name for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
     <span data-ttu-id="556ba-261">**記錄選項**</span><span class="sxs-lookup"><span data-stu-id="556ba-261">**Logging options**</span></span>  
     <span data-ttu-id="556ba-262">選取是要將記錄資訊儲存在 Windows 事件記錄檔中，還是儲存在文字檔中。</span><span class="sxs-lookup"><span data-stu-id="556ba-262">Select whether to store the logging information in the Windows event log, or in a text file.</span></span>  
  
     <span data-ttu-id="556ba-263">**錯誤記錄檔路徑**</span><span class="sxs-lookup"><span data-stu-id="556ba-263">**Error log file path**</span></span>  
     <span data-ttu-id="556ba-264">提供記錄檔位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="556ba-264">Provide a path for the location of the log file.</span></span> <span data-ttu-id="556ba-265">只有在已選取文字檔案登入選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="556ba-265">This option is only available if the text file logging option is selected.</span></span>  
  
10. <span data-ttu-id="556ba-266">從 **[排程封裝]** 頁面，指定您要讓移動或複製作業開始的時間。</span><span class="sxs-lookup"><span data-stu-id="556ba-266">From the **Schedule the Package** page, specify when you want the move or copy operation to start.</span></span> <span data-ttu-id="556ba-267">如果您不是系統管理員，您必須指定可存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSIS) 封裝執行子系統的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Agent Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="556ba-267">If you are not a system administrator, you must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy account that has access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Package execution subsystem.</span></span>  
  
     <span data-ttu-id="556ba-268">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="556ba-268">**Run immediately**</span></span>  
     <span data-ttu-id="556ba-269">在您按 **[下一步]** 之後，開始移動或複製作業。</span><span class="sxs-lookup"><span data-stu-id="556ba-269">Start the move or copy operation after you click **Next**.</span></span>  
  
     <span data-ttu-id="556ba-270">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="556ba-270">**Schedule**</span></span>  
     <span data-ttu-id="556ba-271">稍後開始移動或複製作業。</span><span class="sxs-lookup"><span data-stu-id="556ba-271">Start the move or copy operation later.</span></span> <span data-ttu-id="556ba-272">目前的排程設定會出現在描述方塊中。</span><span class="sxs-lookup"><span data-stu-id="556ba-272">The current schedule settings appear in the description box.</span></span> <span data-ttu-id="556ba-273">若要變更排程，請按一下 **[變更]**。</span><span class="sxs-lookup"><span data-stu-id="556ba-273">To change the schedule, click **Change**.</span></span>  
  
     <span data-ttu-id="556ba-274">**變更**</span><span class="sxs-lookup"><span data-stu-id="556ba-274">**Change**</span></span>  
     <span data-ttu-id="556ba-275">開啟 **[新增作業排程]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="556ba-275">Open the **New Job Schedule** dialog box.</span></span>  
  
     <span data-ttu-id="556ba-276">**Integration Services Proxy 帳戶**</span><span class="sxs-lookup"><span data-stu-id="556ba-276">**Integration Services proxy account**</span></span>  
     <span data-ttu-id="556ba-277">選取可用的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="556ba-277">Select an available proxy account.</span></span> <span data-ttu-id="556ba-278">若要排程傳送，至少必須有一個 Proxy 帳戶可供使用者使用，而且帳戶要設定為擁有 **[SQL Server Integration Services 封裝執行]** 子系統的權限。</span><span class="sxs-lookup"><span data-stu-id="556ba-278">To schedule the transfer, there must be at least one proxy account available to the user, configured with permission to the **SQL Server Integration Services package execution** subsystem.</span></span>  
  
     <span data-ttu-id="556ba-279">若要建立 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝執行的 Proxy 帳戶，請在 [物件總管] 中，展開 **[SQL Server Agent]**、展開 **[Proxy]**、以滑鼠右鍵按一下 **[SSIS 封裝執行]**，然後按一下 **[新增 Proxy]**。</span><span class="sxs-lookup"><span data-stu-id="556ba-279">To create a proxy account for [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution, in Object Explorer, expand **SQL Server Agent**, expand **Proxies**, right-click **SSIS Package Execution**, and then click **New Proxy**.</span></span>  
  
     <span data-ttu-id="556ba-280">**[系統管理員 (sysadmin)]** 固定伺服器角色成員的使用者，可以選取具有必要權限的 **[SQL Server Agent 服務帳戶]** 來執行這個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="556ba-280">Members of the **sysadmin** fixed server role can select the **SQL Server Agent Service Account**, which has the necessary permissions.</span></span>  
  
11. <span data-ttu-id="556ba-281">從 **[完成精靈]** 頁面，檢閱所選選項的摘要。</span><span class="sxs-lookup"><span data-stu-id="556ba-281">From the **Complete the Wizard** page, review the summary of the selected options.</span></span> <span data-ttu-id="556ba-282">按 **[上一步]** 即可變更選項。</span><span class="sxs-lookup"><span data-stu-id="556ba-282">Click **Back** to change an option.</span></span> <span data-ttu-id="556ba-283">按一下 **[完成]** 以建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="556ba-283">Click **Finish** to create the database.</span></span> <span data-ttu-id="556ba-284">在傳送期間， **[正在執行作業]** 頁面會監視有關 **[複製資料庫精靈]** 執行的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="556ba-284">During the transfer, the **Performing operation** page monitors status information about the execution of the **Copy Database Wizard**.</span></span>  
  
     <span data-ttu-id="556ba-285">**動作**</span><span class="sxs-lookup"><span data-stu-id="556ba-285">**Action**</span></span>  
     <span data-ttu-id="556ba-286">列出每個執行的動作。</span><span class="sxs-lookup"><span data-stu-id="556ba-286">Lists each action being performed.</span></span>  
  
     <span data-ttu-id="556ba-287">**狀態**</span><span class="sxs-lookup"><span data-stu-id="556ba-287">**Status**</span></span>  
     <span data-ttu-id="556ba-288">表示動作完全成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="556ba-288">Indicates whether the action as a whole succeeded or failed.</span></span>  
  
     <span data-ttu-id="556ba-289">**Message**</span><span class="sxs-lookup"><span data-stu-id="556ba-289">**Message**</span></span>  
     <span data-ttu-id="556ba-290">提供每個步驟所傳回的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="556ba-290">Provides any messages returned from each step.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="556ba-291">後續操作：升級 SQL Server 資料庫之後</span><span class="sxs-lookup"><span data-stu-id="556ba-291">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="556ba-292">在您使用複製資料庫精靈，將資料庫從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之後，資料庫就會變成立即可用並自動進行升級。</span><span class="sxs-lookup"><span data-stu-id="556ba-292">After you use the Copy Database Wizard to upgrade a database from an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="556ba-293">如果資料庫具有全文檢索索引，升級程序就會根據 [全文檢索目錄升級選項] 伺服器屬性的設定，匯入、重設或重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="556ba-293">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="556ba-294">如果升級選項設定為 [匯入] 或 [重建]，則全文檢索索引在升級期間將無法使用。</span><span class="sxs-lookup"><span data-stu-id="556ba-294">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="556ba-295">根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="556ba-295">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="556ba-296">此外，請注意，當升級選項設定為 [匯入] 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="556ba-296">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="556ba-297">如需有關檢視或變更 **全文檢索目錄升級選項** 屬性設定的詳細資訊，請參閱＜ [管理及監視伺服器執行個體的全文檢索搜尋](../search/manage-and-monitor-full-text-search-for-a-server-instance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="556ba-297">For information about viewing or changing the setting of the **Full-Text Upgrade Option** property, see [Manage and Monitor Full-Text Search for a Server Instance](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).</span></span>  
  
 <span data-ttu-id="556ba-298">如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。</span><span class="sxs-lookup"><span data-stu-id="556ba-298">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="556ba-299">如果已升級資料庫中的相容性層級為 90，則相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所支援的最低相容性層級)。</span><span class="sxs-lookup"><span data-stu-id="556ba-299">If the compatibility level was 90 in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="556ba-300">如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="556ba-300">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556ba-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="556ba-301">See Also</span></span>  
 <span data-ttu-id="556ba-302">[使用卸離和附加 &#40;Transact-sql&#41;升級資料庫](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="556ba-302">[Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span></span>  
 [<span data-ttu-id="556ba-303">建立 SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="556ba-303">Create a SQL Server Agent Proxy</span></span>](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
