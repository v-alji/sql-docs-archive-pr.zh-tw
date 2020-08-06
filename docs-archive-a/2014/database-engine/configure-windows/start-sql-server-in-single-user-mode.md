---
title: 以單一使用者模式啟動 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b2600524da45f9a81f155432397cee2e7e876274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585576"
---
# <a name="start-sql-server-in-single-user-mode"></a><span data-ttu-id="c02a6-102">以單一使用者模式啟動 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c02a6-102">Start SQL Server in Single-User Mode</span></span>
  <span data-ttu-id="c02a6-103">在某些情況下，您可能需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup option -m **，在單一使用者模式下啟動**的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c02a6-103">Under certain circumstances, you may have to start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode by using the **startup option -m.**</span></span> <span data-ttu-id="c02a6-104">例如，您可能想要變更伺服器組態選項，或復原損毀的 master 資料庫或其他系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="c02a6-104">For example, you may want to change server configuration options or recover a damaged master database or other system database.</span></span> <span data-ttu-id="c02a6-105">這兩個動作都需要在單一使用者模式下啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c02a6-105">Both actions require starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>  
  
 <span data-ttu-id="c02a6-106">在單一使用者模式下啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可讓電腦本機管理員群組的任何成員以 sysadmin 固定伺服器角色的成員身分，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c02a6-106">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="c02a6-107">如需詳細資訊，請參閱 [當系統管理員遭到鎖定時連接到 SQL Server](connect-to-sql-server-when-system-administrators-are-locked-out.md)。</span><span class="sxs-lookup"><span data-stu-id="c02a6-107">For more information, see [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md).</span></span>  
  
 <span data-ttu-id="c02a6-108">以單一使用者模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="c02a6-108">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, note the following:</span></span>  
  
-   <span data-ttu-id="c02a6-109">只有一個使用者可以連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="c02a6-109">Only one user can connect to the server.</span></span>  
  
-   <span data-ttu-id="c02a6-110">不會執行 CHECKPOINT 處理。</span><span class="sxs-lookup"><span data-stu-id="c02a6-110">The CHECKPOINT process is not executed.</span></span> <span data-ttu-id="c02a6-111">依預設，在啟動時會自動執行。</span><span class="sxs-lookup"><span data-stu-id="c02a6-111">By default, it is executed automatically at startup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c02a6-112">連接到單一使用者模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之前必須先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，否則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務會使用該連接，從而將其封鎖。</span><span class="sxs-lookup"><span data-stu-id="c02a6-112">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode; otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service uses the connection, thereby blocking it.</span></span>  
  
 <span data-ttu-id="c02a6-113">以單一使用者模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 可以連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c02a6-113">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c02a6-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的物件總管可能會失敗，因為它需要一個以上的連接才能進行某些作業。</span><span class="sxs-lookup"><span data-stu-id="c02a6-114">Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] might fail because it requires more than one connection for some operations.</span></span> <span data-ttu-id="c02a6-115">若要在單一使用者模式下管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，僅透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的查詢編輯器連接來執行 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，或使用 [sqlcmd 公用程式](../../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="c02a6-115">To manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by connecting only through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or use the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="c02a6-116">當您搭配**sqlcmd**或使用 **-m**選項時 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，可以限制與指定之用戶端應用程式的連接。</span><span class="sxs-lookup"><span data-stu-id="c02a6-116">When you use the **-m** option with **sqlcmd** or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can limit the connections to a specified client application.</span></span> <span data-ttu-id="c02a6-117">例如， **-m "sqlcmd"** 會將連接限制為單一連接，而且該連接必須將自己識別為**sqlcmd**用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="c02a6-117">For example, **-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program.</span></span> <span data-ttu-id="c02a6-118">當您在單一使用者模式下啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而且有未知的用戶端應用程式佔用唯一可用的連接時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="c02a6-118">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="c02a6-119">若要透過 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的查詢編輯器進行連接，請使用 **-m"Microsoft SQL Server Management Studio - Query"** 。</span><span class="sxs-lookup"><span data-stu-id="c02a6-119">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c02a6-120">請勿將這個選項當做安全性功能使用。</span><span class="sxs-lookup"><span data-stu-id="c02a6-120">Do not use this option as a security feature.</span></span> <span data-ttu-id="c02a6-121">用戶端應用程式會提供用戶端應用程式名稱，而且可能會在連接字串中提供假的名稱。</span><span class="sxs-lookup"><span data-stu-id="c02a6-121">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>  
  
## <a name="note-for-clustered-installations"></a><span data-ttu-id="c02a6-122">叢集安裝注意事項</span><span class="sxs-lookup"><span data-stu-id="c02a6-122">Note for Clustered installations</span></span>  
 <span data-ttu-id="c02a6-123">如果是叢集環境中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在單一使用者模式下啟動時，叢集資源 dll 會用完可用的連接，藉此封鎖與伺服器的任何其他連接。</span><span class="sxs-lookup"><span data-stu-id="c02a6-123">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in a clustered environment, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started in single user mode, the cluster resource dll uses up the available connection thereby blocking any other connections to the server.</span></span> <span data-ttu-id="c02a6-124">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在此狀態下時，如果您嘗試將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 資源帶到線上，當 SQL 資源設定為可影響群組時，它可能會將此資源容錯移轉到另一個節點。</span><span class="sxs-lookup"><span data-stu-id="c02a6-124">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in this state, if you try to bring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resource online, it may fail over the SQL resource to a different node if the resource is configured to affect the group.</span></span>  
  
 <span data-ttu-id="c02a6-125">若要避開此問題，請使用下列程序：</span><span class="sxs-lookup"><span data-stu-id="c02a6-125">To get around the problem use the following procedure:</span></span>  
  
1.  <span data-ttu-id="c02a6-126">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進階屬性中移除 -m 啟動參數。</span><span class="sxs-lookup"><span data-stu-id="c02a6-126">Remove the -m startup parameter from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] advanced Properties.</span></span>  
  
2.  <span data-ttu-id="c02a6-127">讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源離線。</span><span class="sxs-lookup"><span data-stu-id="c02a6-127">Take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline.</span></span>  
  
3.  <span data-ttu-id="c02a6-128">從這個群組的目前擁有者節點，從命令提示字元發出下列命令：</span><span class="sxs-lookup"><span data-stu-id="c02a6-128">From the current owner node of this group, issue the following command from the command prompt:</span></span>  
    <span data-ttu-id="c02a6-129">net start MSSQLSERVER /m</span><span class="sxs-lookup"><span data-stu-id="c02a6-129">net start MSSQLSERVER /m.</span></span>  
  
4.  <span data-ttu-id="c02a6-130">從叢集管理員或是容錯移轉叢集管理主控台確認 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源依然為離線狀態。</span><span class="sxs-lookup"><span data-stu-id="c02a6-130">Verify from the cluster administrator or failover cluster management console that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource is still offline.</span></span>  
  
5.  <span data-ttu-id="c02a6-131">現在使用下列命令連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，並執行必要作業：SQLCMD -E -S\<servername>。</span><span class="sxs-lookup"><span data-stu-id="c02a6-131">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] now using the following command and do the necessary operation: SQLCMD -E -S\<servername>.</span></span>  
  
6.  <span data-ttu-id="c02a6-132">當此操作完成之後，關閉命令提示字元，並透過叢集管理員將 SQL 和其他資源帶回線上。</span><span class="sxs-lookup"><span data-stu-id="c02a6-132">Once the operation is complete, close the command prompt and bring back the SQL and other resources online through cluster administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02a6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c02a6-133">See Also</span></span>  
 <span data-ttu-id="c02a6-134">[啟動、停止或暫停 SQL Server Agent 服務](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="c02a6-134">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="c02a6-135">[資料庫管理員的診斷連接](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="c02a6-135">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="c02a6-136">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c02a6-136">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="c02a6-137">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c02a6-137">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span></span>  
 <span data-ttu-id="c02a6-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c02a6-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c02a6-139">Database Engine 服務啟動選項</span><span class="sxs-lookup"><span data-stu-id="c02a6-139">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
