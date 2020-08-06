---
title: 連接到伺服器 (資料庫引擎) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca227d1a3bbc13160962ba2fcad23ff011c950f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702313"
---
# <a name="connect-to-server-database-engine"></a><span data-ttu-id="02644-102">連接到伺服器 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="02644-102">Connect to Server (Database Engine)</span></span>
  <span data-ttu-id="02644-103">連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 時，使用此對話方塊來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="02644-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="02644-104">在大多數的情況下，您可以在 [伺服器名稱] 方塊中輸入資料庫伺服器的電腦名稱，然後按一下 [連接] 來進行連接。</span><span class="sxs-lookup"><span data-stu-id="02644-104">In most cases, you can connect by entering the computer name of the database server in the **Server name** box and then clicking **Connect**.</span></span> <span data-ttu-id="02644-105">如果要連接到 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]，請使用電腦名稱並於後面加上 **\sqlexpress**。</span><span class="sxs-lookup"><span data-stu-id="02644-105">If you are connecting to [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], use the computer name followed by **\sqlexpress**.</span></span>  
  
 <span data-ttu-id="02644-106">許多因素都可能影響連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的能力。</span><span class="sxs-lookup"><span data-stu-id="02644-106">Many factors can affect your ability to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="02644-107">選項。</span><span class="sxs-lookup"><span data-stu-id="02644-107">Options</span></span>  
 <span data-ttu-id="02644-108">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="02644-108">**Server type**</span></span>  
 <span data-ttu-id="02644-109">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02644-109">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="02644-110">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="02644-110">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="02644-111">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型] 方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="02644-111">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="02644-112">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [ [!INCLUDE[ssDE](../../includes/ssde-md.md)]]、[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]]、[ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]]、[ [!INCLUDE[ssEW](../../includes/ssew-md.md)]] 或 [ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="02644-112">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="02644-113">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="02644-113">**Server name**</span></span>  
 <span data-ttu-id="02644-114">選取要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="02644-114">Select the server instance to connect to.</span></span> <span data-ttu-id="02644-115">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="02644-115">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02644-116">若要連接到 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 的使用中使用者執行個體，請使用指定管道名稱的具名管道通訊協定進行連接，例如 np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query。如需詳細資訊，請參閱 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="02644-116">To connect to an active user instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] connect using named pipes protocol specifying the pipe name, such as np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query For more information, see the [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="02644-117">**驗證**</span><span class="sxs-lookup"><span data-stu-id="02644-117">**Authentication**</span></span>  
 <span data-ttu-id="02644-118">當連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體時，有兩種可用的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="02644-118">Two authentication modes are available when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="02644-119">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="02644-119">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="02644-120">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="02644-120">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="02644-121">**SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="02644-121">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="02644-122">當使用者從非信任連接以指定的登入名稱與密碼進行連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會查看是否已設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="02644-122">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="02644-123">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 沒有登入帳戶集，驗證將失敗，而使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="02644-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02644-124">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="02644-124">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="02644-125">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="02644-125">**User name**</span></span>  
 <span data-ttu-id="02644-126">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="02644-126">Enter the user name to connect with.</span></span> <span data-ttu-id="02644-127">只有在您選取使用 Windows 驗證連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="02644-127">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="02644-128">**登入**</span><span class="sxs-lookup"><span data-stu-id="02644-128">**Login**</span></span>  
 <span data-ttu-id="02644-129">輸入要用來連接的登入。</span><span class="sxs-lookup"><span data-stu-id="02644-129">Enter the login to connect with.</span></span> <span data-ttu-id="02644-130">這個選項只有在您選取了使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時才可以使用。</span><span class="sxs-lookup"><span data-stu-id="02644-130">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="02644-131">**密碼**</span><span class="sxs-lookup"><span data-stu-id="02644-131">**Password**</span></span>  
 <span data-ttu-id="02644-132">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="02644-132">Enter the password for the login.</span></span> <span data-ttu-id="02644-133">只有在您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="02644-133">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="02644-134">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="02644-134">**Connect**</span></span>  
 <span data-ttu-id="02644-135">按一下即可連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="02644-135">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="02644-136">**選項**</span><span class="sxs-lookup"><span data-stu-id="02644-136">**Options**</span></span>  
 <span data-ttu-id="02644-137">按一下即可顯示其他伺服器連接選項，例如，註冊伺服器與記住密碼。</span><span class="sxs-lookup"><span data-stu-id="02644-137">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
