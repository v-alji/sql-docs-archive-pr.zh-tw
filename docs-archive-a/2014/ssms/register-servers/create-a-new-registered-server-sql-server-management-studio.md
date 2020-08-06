---
title: 建立新的已註冊伺服器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.sqlce.f1
- sql12.swb.registerserver.general.sqlserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], creating new registered servers
ms.assetid: 716ea070-a3b5-4514-9de2-82ce8a96514b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 43cdb06179531a739f6595dc5ade9eeb79ea65ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584251"
---
# <a name="create-a-new-registered-server-sql-server-management-studio"></a><span data-ttu-id="48137-102">建立新的已註冊伺服器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="48137-102">Create a New Registered Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="48137-103">本主題描述如何藉由在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中於 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的「已註冊的伺服器」元件中註冊伺服器，來儲存您經常存取之伺服器的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="48137-103">This topic describes how to save the connection information for servers that you access frequently, by registering the server in the Registered Servers component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="48137-104">您可以在連接之前或在連接時從 [物件總管] 註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="48137-104">A server can be registered before connecting, or when connecting from Object Explorer.</span></span> <span data-ttu-id="48137-105">有一個特定的功能表選項，可用來註冊本機電腦上的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="48137-105">There is a special menu option to register the server instances on the local computer.</span></span>  
  
 <span data-ttu-id="48137-106">已註冊的伺服器有兩種：</span><span class="sxs-lookup"><span data-stu-id="48137-106">There are two kinds of registered servers:</span></span>  
  
-   <span data-ttu-id="48137-107">本機伺服器群組</span><span class="sxs-lookup"><span data-stu-id="48137-107">Local server groups</span></span>  
  
     <span data-ttu-id="48137-108">使用本機伺服器群組可輕鬆地連接您經常管理的伺服器。</span><span class="sxs-lookup"><span data-stu-id="48137-108">Use local server groups to easily connect to servers that you frequently manage.</span></span> <span data-ttu-id="48137-109">本機伺服器和非本機伺服器都會在本機伺服器群組中註冊。</span><span class="sxs-lookup"><span data-stu-id="48137-109">Both local and non-local servers are registered into local server groups.</span></span> <span data-ttu-id="48137-110">本機伺服器群組對於每一位使用者而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="48137-110">Local server groups are unique to each user.</span></span> <span data-ttu-id="48137-111">如需如何共用已註冊之伺服器的相關資訊，請參閱 [匯出已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) 和 [匯入已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)的「已註冊的伺服器」元件中註冊伺服器，來儲存您經常存取之伺服器的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="48137-111">For information about how to share registered server information, see [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) and [Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48137-112">我們建議您盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="48137-112">We recommend that you use Windows Authentication whenever possible.</span></span>  
  
-   <span data-ttu-id="48137-113">中央管理伺服器</span><span class="sxs-lookup"><span data-stu-id="48137-113">Central Management Servers</span></span>  
  
     <span data-ttu-id="48137-114">中央管理伺服器會將伺服器組態儲存在中央管理伺服器中，而不是檔案系統上。</span><span class="sxs-lookup"><span data-stu-id="48137-114">Central Management Servers store server registrations in the Central Management Server instead of on the file system.</span></span> <span data-ttu-id="48137-115">中央管理伺服器和從屬的已註冊伺服器只能使用 Windows 驗證來註冊。</span><span class="sxs-lookup"><span data-stu-id="48137-115">Central Management Servers and subordinate registered servers can be registered only by using Windows Authentication.</span></span> <span data-ttu-id="48137-116">在註冊中央管理伺服器之後，其關聯的已註冊伺服器將會自動顯示。</span><span class="sxs-lookup"><span data-stu-id="48137-116">After a Central Management Server has been registered, its associated registered servers will be automatically displayed.</span></span> <span data-ttu-id="48137-117">如需中央管理伺服器的詳細資訊，請參閱 [使用中央管理伺服器管理多部伺服器](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="48137-117">For more information about Central Management Servers, see [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span> <span data-ttu-id="48137-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本無法指定為中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="48137-118">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="48137-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="48137-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-register-the-local-server-instances"></a><span data-ttu-id="48137-120">自動註冊本機伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="48137-120">To automatically register the local server instances</span></span>  
  
-   <span data-ttu-id="48137-121">在 [已註冊的伺服器] 中，以滑鼠右鍵按一下 [已註冊的伺服器] 樹狀目錄的任何節點，然後按一下 [更新本機伺服器註冊]  。</span><span class="sxs-lookup"><span data-stu-id="48137-121">In Registered Servers, right-click any node in the Registered Servers tree, and then click **Update Local Server Registration**.</span></span>  
  
#### <a name="to-create-a-new-registered-server"></a><span data-ttu-id="48137-122">建立新的已註冊伺服器</span><span class="sxs-lookup"><span data-stu-id="48137-122">To create a new registered server</span></span>  
  
1.  <span data-ttu-id="48137-123">如果在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中看不到「已註冊的伺服器」，請在 **[檢視]** 功能表上按一下 **[已註冊的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="48137-123">If Registered Servers is not visible in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="48137-124">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="48137-124">**Server type**</span></span>  
     <span data-ttu-id="48137-125">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型]  方塊是唯讀的，且會與 [已註冊的伺服器] 窗格中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="48137-125">When a server is registered from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers pane.</span></span> <span data-ttu-id="48137-126">若要註冊不同類型的伺服器，請在 **[已註冊的伺服器]** 工具列上按一下 **[Database Engine]** 、 **[Analysis Server]** 、 **[Reporting Services]** 或 **[Integration Services]** ，然後再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="48137-126">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
     <span data-ttu-id="48137-127">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="48137-127">**Server name**</span></span>  
     <span data-ttu-id="48137-128">選取要以下列格式註冊的伺服器實例： *\<servername>* [ \\ *\<instancename>* ]。</span><span class="sxs-lookup"><span data-stu-id="48137-128">Select the server instance to register in the format: *\<servername>*[\\*\<instancename>*].</span></span>  
  
     <span data-ttu-id="48137-129">**驗證**</span><span class="sxs-lookup"><span data-stu-id="48137-129">**Authentication**</span></span>  
     <span data-ttu-id="48137-130">當連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體時，有兩種可用的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="48137-130">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="48137-131">**Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="48137-131">**Windows Authentication**</span></span>  
     <span data-ttu-id="48137-132">Windows 驗證模式允許使用者透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="48137-132">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="48137-133">**SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="48137-133">**SQL Server Authentication**</span></span>  
     <span data-ttu-id="48137-134">當使用者從非信任連接使用指定的登入名稱與密碼進行連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會查看是否已設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="48137-134">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="48137-135">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 沒有登入帳戶集，驗證將失敗，而使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="48137-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)] <span data-ttu-id="48137-136">如需詳細資訊，請參閱 [選擇驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="48137-136">For more information, see [Choose an Authentication Mode](../../relational-databases/security/choose-an-authentication-mode.md).</span></span>  
  
     <span data-ttu-id="48137-137">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="48137-137">**User name**</span></span>  
     <span data-ttu-id="48137-138">顯示您所連接的目前使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="48137-138">Shows the current user name you are connecting with.</span></span> <span data-ttu-id="48137-139">只有在您已選取使用 Windows 驗證進行連接時，才能使用此唯讀選項。</span><span class="sxs-lookup"><span data-stu-id="48137-139">This read-only option is only available if you have selected to connect using Windows Authentication.</span></span> <span data-ttu-id="48137-140">若要變更 **[使用者名稱]** ，請以不同使用者登入電腦。</span><span class="sxs-lookup"><span data-stu-id="48137-140">To change **User names**, log in to the computer as a different user.</span></span>  
  
     <span data-ttu-id="48137-141">**登入**</span><span class="sxs-lookup"><span data-stu-id="48137-141">**Login**</span></span>  
     <span data-ttu-id="48137-142">輸入要用來連接的登入。</span><span class="sxs-lookup"><span data-stu-id="48137-142">Enter the login to connect with.</span></span> <span data-ttu-id="48137-143">只有在您已選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="48137-143">This option is available only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="48137-144">**密碼**</span><span class="sxs-lookup"><span data-stu-id="48137-144">**Password**</span></span>  
     <span data-ttu-id="48137-145">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="48137-145">Enter the password for the login.</span></span> <span data-ttu-id="48137-146">只有在您已選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接時，才可以編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="48137-146">This option can be edited only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="48137-147">**記住密碼**</span><span class="sxs-lookup"><span data-stu-id="48137-147">**Remember password**</span></span>  
     <span data-ttu-id="48137-148">選取即可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 加密和儲存您輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="48137-148">Select to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypt and store the password you have entered.</span></span> <span data-ttu-id="48137-149">只有在您已選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="48137-149">This option is displayed only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48137-150">如果您已儲存密碼而要停止儲存密碼，請清除此核取方塊，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="48137-150">If you have stored the password and want to stop storing it, clear this check box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="48137-151">**已註冊的伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="48137-151">**Registered server name**</span></span>  
     <span data-ttu-id="48137-152">您要在 [已註冊的伺服器] 上顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="48137-152">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="48137-153">此名稱不需要與 **[伺服器名稱]** 方塊中的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="48137-153">This name does not have to match the **Server name** box.</span></span>  
  
     <span data-ttu-id="48137-154">**已註冊的伺服器描述**</span><span class="sxs-lookup"><span data-stu-id="48137-154">**Registered server description**</span></span>  
     <span data-ttu-id="48137-155">輸入伺服器的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="48137-155">Enter an optional description of the server.</span></span>  
  
     <span data-ttu-id="48137-156">**Test**</span><span class="sxs-lookup"><span data-stu-id="48137-156">**Test**</span></span>  
     <span data-ttu-id="48137-157">按一下以測試與 [伺服器名稱]  中選取之伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="48137-157">Click to test the connection to the server selected in **Server name**.</span></span>  
  
     <span data-ttu-id="48137-158">**儲存**</span><span class="sxs-lookup"><span data-stu-id="48137-158">**Save**</span></span>  
     <span data-ttu-id="48137-159">按一下即可儲存已註冊的伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="48137-159">Click to save the registered server settings.</span></span>  
  
## <a name="multiserver-queries"></a><span data-ttu-id="48137-160">多伺服器查詢</span><span class="sxs-lookup"><span data-stu-id="48137-160">Multiserver Queries</span></span>  
 <span data-ttu-id="48137-161">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [查詢編輯器] 視窗可以同時連接及查詢多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="48137-161">The Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to and query multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the same time.</span></span> <span data-ttu-id="48137-162">此查詢傳回的結果可以合併到單一結果窗格，或者可以在不同的結果窗格中傳回。</span><span class="sxs-lookup"><span data-stu-id="48137-162">The results that are returned by the query can be merged into a single results pane, or they can be returned in separate results panes.</span></span> <span data-ttu-id="48137-163">還有一個選擇如下：[查詢編輯器] 所包含的資料行可提供產生每一個資料列的伺服器名稱，以及連接到提供每一個資料列之伺服器所用的登入。</span><span class="sxs-lookup"><span data-stu-id="48137-163">As an option, Query Editor can include columns that provide the name of the server that produced each row, and also the login that was used to connect to the server that provided each row.</span></span> <span data-ttu-id="48137-164">如需如何執行多伺服器查詢的詳細資訊，請參閱[同時對多部伺服器執行陳述式 &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)。</span><span class="sxs-lookup"><span data-stu-id="48137-164">For more information about how to execute multiserver queries, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
 <span data-ttu-id="48137-165">若要針對本機伺服器群組內的所有伺服器執行查詢，請以滑鼠右鍵按一下伺服器群組，並指向 [連接]  ，然後按一下 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="48137-165">To execute queries against all the servers in a local server group, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="48137-166">在新的 [查詢編輯器] 視窗中執行查詢時，將會使用包含使用者驗證內容的預存連接資訊，針對此群組中的所有伺服器來執行。</span><span class="sxs-lookup"><span data-stu-id="48137-166">When queries are executed in the new Query Editor window, they will execute against all servers in the group, using the stored connection information including the user authentication context.</span></span> <span data-ttu-id="48137-167">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證所註冊但是未儲存密碼的伺服器將會連接失敗。</span><span class="sxs-lookup"><span data-stu-id="48137-167">Servers registered by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but not saving the password will fail to connect.</span></span>  
  
 <span data-ttu-id="48137-168">若要針對使用中央管理伺服器註冊的所有伺服器執行查詢，請展開中央管理伺服器，然後以滑鼠右鍵按一下伺服器群組，並指向 [連接]  ，再按一下 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="48137-168">To execute queries against all the servers that are registered with a Central Management Server, expand the Central Management Server, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="48137-169">在新的 [查詢編輯器] 視窗中執行查詢時，將會使用預存連接資訊及使用者的 Windows 驗證內容，針對此伺服器群組中的所有伺服器來執行。</span><span class="sxs-lookup"><span data-stu-id="48137-169">When queries are executed in the new Query Editor window, they will execute against all of the servers in the server group, using the stored connection information and using the Windows Authentication context of the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48137-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48137-170">See Also</span></span>  
 <span data-ttu-id="48137-171">[在物件總管中隱藏系統物件](../object/hide-system-objects-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="48137-171">[Hide System Objects in Object Explorer](../object/hide-system-objects-in-object-explorer.md) </span></span>  
 <span data-ttu-id="48137-172">[匯出已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="48137-172">[Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="48137-173">匯入已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="48137-173">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)  
  
  
