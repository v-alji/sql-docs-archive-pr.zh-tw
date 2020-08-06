---
title: 連接到伺服器 (登入頁面) 資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665a5c491b0bea1145c60d15f1006de97281a30d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702314"
---
# <a name="connect-to-server-login-page-database-engine"></a><span data-ttu-id="85193-102">連接到伺服器 (登入頁面) Database Engine</span><span class="sxs-lookup"><span data-stu-id="85193-102">Connect to Server (Login Page) Database Engine</span></span>
  <span data-ttu-id="85193-103">使用此索引標籤來檢視或指定連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 時的選項。</span><span class="sxs-lookup"><span data-stu-id="85193-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85193-104">若要連結 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，必須以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 驗證模式設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85193-104">To connect with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode.</span></span> <span data-ttu-id="85193-105">如需如何判斷驗證模式及變更驗證模式的詳細資訊，請參閱[變更伺服器驗證模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="85193-105">For more information about how to determine the authentication mode and to change the authentication mode, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="85193-106">選項。</span><span class="sxs-lookup"><span data-stu-id="85193-106">Options</span></span>  
 <span data-ttu-id="85193-107">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="85193-107">**Server type**</span></span>  
 <span data-ttu-id="85193-108">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="85193-108">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="85193-109">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="85193-109">The rest of the dialog box shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="85193-110">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型]  方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="85193-110">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="85193-111">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [[!INCLUDE[ssDE](../../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services] 或 [Integration Services]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="85193-111">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="85193-112">當您透過 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine 執行個體時，您必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，並在 [連接到伺服器]  對話方塊的 [連接屬性]  索引標籤上指定資料庫。請務必選取 [加密連接]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="85193-112">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="85193-113">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會連接到 **master**。</span><span class="sxs-lookup"><span data-stu-id="85193-113">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="85193-114">如果您指定使用者資料庫，您只會在物件總管中看到該資料庫與其物件。</span><span class="sxs-lookup"><span data-stu-id="85193-114">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="85193-115">如果您連接到 **master**，您將能夠看到所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="85193-115">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="85193-116">如需詳細資訊，請參閱[Azure SQL Database 總覽](/azure/sql-database/sql-database-technical-overview)。</span><span class="sxs-lookup"><span data-stu-id="85193-116">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="85193-117">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="85193-117">**Server name**</span></span>  
 <span data-ttu-id="85193-118">選取要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="85193-118">Select the server instance to connect to.</span></span> <span data-ttu-id="85193-119">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="85193-119">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="85193-120">**驗證**</span><span class="sxs-lookup"><span data-stu-id="85193-120">**Authentication**</span></span>  
 <span data-ttu-id="85193-121">當連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體時，有兩種可用的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="85193-121">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="85193-122">當您透過 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine 執行個體時，您必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，並在 [連接到伺服器]  對話方塊的 [連接屬性]  索引標籤上指定資料庫。請務必選取 [加密連接]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="85193-122">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="85193-123">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會連接到 **master**。</span><span class="sxs-lookup"><span data-stu-id="85193-123">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="85193-124">如果您指定使用者資料庫，您只會在物件總管中看到該資料庫與其物件。</span><span class="sxs-lookup"><span data-stu-id="85193-124">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="85193-125">如果您連接到 **master**，您將能夠看到所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="85193-125">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="85193-126">如需詳細資訊，請參閱[Azure SQL Database 總覽](/azure/sql-database/sql-database-technical-overview)。</span><span class="sxs-lookup"><span data-stu-id="85193-126">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="85193-127">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="85193-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="85193-128">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="85193-128">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="85193-129">**SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="85193-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="85193-130">當使用者從非信任連接以指定的登入名稱與密碼進行連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會查看是否已設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="85193-130">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="85193-131">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 沒有登入帳戶集，驗證將失敗，而使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="85193-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85193-132">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="85193-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="85193-133">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="85193-133">**User name**</span></span>  
 <span data-ttu-id="85193-134">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="85193-134">Enter the user name to connect with.</span></span> <span data-ttu-id="85193-135">只有在您選取使用 Windows 驗證連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="85193-135">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="85193-136">**登入**</span><span class="sxs-lookup"><span data-stu-id="85193-136">**Login**</span></span>  
 <span data-ttu-id="85193-137">輸入要用來連接的登入。</span><span class="sxs-lookup"><span data-stu-id="85193-137">Enter the login to connect with.</span></span> <span data-ttu-id="85193-138">這個選項只有在您選取了使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時才可以使用。</span><span class="sxs-lookup"><span data-stu-id="85193-138">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="85193-139">**密碼**</span><span class="sxs-lookup"><span data-stu-id="85193-139">**Password**</span></span>  
 <span data-ttu-id="85193-140">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="85193-140">Enter the password for the login.</span></span> <span data-ttu-id="85193-141">只有在您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="85193-141">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="85193-142">**記住密碼**</span><span class="sxs-lookup"><span data-stu-id="85193-142">**Remember password**</span></span>  
 <span data-ttu-id="85193-143">按一下即可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 儲存您輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="85193-143">Click to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] store the password you have entered.</span></span> <span data-ttu-id="85193-144">只有在您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時，才能顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="85193-144">This option is only displayed if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="85193-145">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="85193-145">**Connect**</span></span>  
 <span data-ttu-id="85193-146">按一下即可連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="85193-146">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="85193-147">**選項**</span><span class="sxs-lookup"><span data-stu-id="85193-147">**Options**</span></span>  
 <span data-ttu-id="85193-148">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="85193-148">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
