---
title: 建立中央管理伺服器和群組
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- configuration server
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f53b75966a14dbc6fd6cdc9bea0929ccac7780c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686730"
---
# <a name="create-a-central-management-server-and-server-group-sql-server-management-studio"></a><span data-ttu-id="f82fa-102">建立中央管理伺服器與伺服器群組 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f82fa-102">Create a Central Management Server and Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f82fa-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體指定為 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-103">This topic describes how to designate an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a central management server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f82fa-104">中央管理伺服器會儲存組織成一個或多個中央管理伺服器群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體清單。</span><span class="sxs-lookup"><span data-stu-id="f82fa-104">Central management servers store a list of instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is organized into one or more central management server groups.</span></span> <span data-ttu-id="f82fa-105">使用中央管理伺服器群組所採取的動作將會在伺服器群組中的所有伺服器上運作。</span><span class="sxs-lookup"><span data-stu-id="f82fa-105">Actions that are taken by using a central management server group act on all servers in the server group.</span></span> <span data-ttu-id="f82fa-106">這包括使用 [物件總管] 來連接至伺服器，以及同時在多部伺服器上執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和以原則為基礎的管理原則。</span><span class="sxs-lookup"><span data-stu-id="f82fa-106">This includes connecting to servers by using Object Explorer and executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and Policy-Based Management policies on multiple servers at the same time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f82fa-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本無法指定為中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-107">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a central management server.</span></span>  
  
 <span data-ttu-id="f82fa-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f82fa-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f82fa-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f82fa-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f82fa-110">安全性</span><span class="sxs-lookup"><span data-stu-id="f82fa-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f82fa-111">**使用下列方法建立中央管理伺服器和伺服器群組：**</span><span class="sxs-lookup"><span data-stu-id="f82fa-111">**To create a Central Management Server and Server Group, using:**</span></span>  
  
     [<span data-ttu-id="f82fa-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f82fa-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f82fa-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="f82fa-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f82fa-114">Security</span><span class="sxs-lookup"><span data-stu-id="f82fa-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f82fa-115">權限</span><span class="sxs-lookup"><span data-stu-id="f82fa-115">Permissions</span></span>  
 <span data-ttu-id="f82fa-116">msdb 資料庫中的兩個資料庫角色會授與中央管理伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="f82fa-116">Two database roles in the msdb database grant access to central management servers.</span></span> <span data-ttu-id="f82fa-117">只有 ServerGroupAdministratorRole 角色的成員可以管理中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-117">Only members of the ServerGroupAdministratorRole role can manage the central management server.</span></span> <span data-ttu-id="f82fa-118">您需要 ServerGroupReaderRole 角色的成員資格才能連接至中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-118">Membership in the ServerGroupReaderRole role is required to connect to a central management server.</span></span>  
  
 <span data-ttu-id="f82fa-119">由於中央管理伺服器所維護的連接會在使用者的內容中執行，所以使用 Windows 驗證時，已註冊之伺服器上的有效權限可能會不同。</span><span class="sxs-lookup"><span data-stu-id="f82fa-119">Because the connections that are maintained by a central management server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="f82fa-120">例如，雖然使用者可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員，但是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 執行個體上具有有限的權限。</span><span class="sxs-lookup"><span data-stu-id="f82fa-120">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f82fa-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f82fa-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f82fa-122">下列程序描述如何執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="f82fa-122">The following procedures describe how to perform the following steps.</span></span>  
  
1.  <span data-ttu-id="f82fa-123">建立中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-123">Create a central management server.</span></span>  
  
2.  <span data-ttu-id="f82fa-124">將一個或多個伺服器群組加入至中央管理伺服器，並將一個或多個已註冊的伺服器加入至伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="f82fa-124">Add one or more server groups to the central management server and add one or more registered servers to the server groups.</span></span>  
  
#### <a name="create-a-central-management-server"></a><span data-ttu-id="f82fa-125">建立中央管理伺服器</span><span class="sxs-lookup"><span data-stu-id="f82fa-125">Create a central management server</span></span>  
  
1.  <span data-ttu-id="f82fa-126">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **[檢視]** 功能表中，按一下 **[已註冊的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="f82fa-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="f82fa-127">在 [已註冊的伺服器] 中，展開 [Database Engine]  ，以滑鼠右鍵按一下 [中央管理伺服器]  ，然後按一下 [註冊中央管理伺服器]  。</span><span class="sxs-lookup"><span data-stu-id="f82fa-127">In Registered Servers, expand **Database Engine**, right-click **Central Management Servers**, and then  click **Register Central Management Server**.</span></span>  
  
3.  <span data-ttu-id="f82fa-128">在 [新增伺服器註冊]  對話方塊中，從伺服器下拉式清單中選取您想要成為中央管理伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f82fa-128">In the **New Server Registration** dialog box, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to become the central management server from the drop-down list of servers.</span></span> <span data-ttu-id="f82fa-129">中央管理伺服器必須使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f82fa-129">You must use Windows Authentication for the central management server.</span></span>  
  
4.  <span data-ttu-id="f82fa-130">在 **[已註冊的伺服器]** ，輸入伺服器名稱和選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="f82fa-130">In **Registered Server**, enter a server name and optional description.</span></span>  
  
5.  <span data-ttu-id="f82fa-131">從 **[連接屬性]** 索引標籤，檢閱或修改網路和連接屬性。</span><span class="sxs-lookup"><span data-stu-id="f82fa-131">From the **Connection Properties** tab, review or modifiy the network  and connection properties.</span></span> <span data-ttu-id="f82fa-132">如需詳細資訊，請參閱[連接到伺服器 &#40;連接屬性頁面&#41; Database Engine](../f1-help/connect-to-server-connection-properties-page-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="f82fa-132">For more information, see [Connect to Server &#40;Connection Properties Page&#41; Database Engine](../f1-help/connect-to-server-connection-properties-page-database-engine.md)</span></span>  
  
6.  <span data-ttu-id="f82fa-133">按一下 **[測試]** 測試連接。</span><span class="sxs-lookup"><span data-stu-id="f82fa-133">Click **Test**, to test the connection.</span></span>  
  
7.  <span data-ttu-id="f82fa-134">按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="f82fa-134">Click **Save**.</span></span> <span data-ttu-id="f82fa-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體會出現在 **[中央管理伺服器]** 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="f82fa-135">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will appear under the **Central Management Servers** folder.</span></span>  
  
#### <a name="create-a-new-server-group-and-add-servers-to-the-group"></a><span data-ttu-id="f82fa-136">建立新的伺服器群組並將伺服器加入至群組</span><span class="sxs-lookup"><span data-stu-id="f82fa-136">Create a new server group and add servers to the group</span></span>  
  
1.  <span data-ttu-id="f82fa-137">從 **[已註冊的伺服器]** ，展開 **[中央管理伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="f82fa-137">From **Registered Servers**, expand **Central Management Servers**.</span></span> <span data-ttu-id="f82fa-138">以滑鼠右鍵按一下上述程序中加入的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，然後選取 [新增伺服器群組]  。</span><span class="sxs-lookup"><span data-stu-id="f82fa-138">Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] added in the procedure above and select **New Server Group**.</span></span>  
  
2.  <span data-ttu-id="f82fa-139">在 **[新增伺服器群組屬性]** ，輸入群組名稱和選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="f82fa-139">In **New Server Group Properties**, enter a group name and optional description.</span></span>  
  
3.  <span data-ttu-id="f82fa-140">在 [已註冊的伺服器]  中，以滑鼠右鍵按一下伺服器群組，然後按一下 [新增伺服器註冊]  。</span><span class="sxs-lookup"><span data-stu-id="f82fa-140">From **Registered Servers**, right-click the server group and click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="f82fa-141">從 [新增伺服器註冊]，選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f82fa-141">From New Server Registration, select an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f82fa-142">如需詳細資訊，請參閱[建立新的已註冊伺服器 &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="f82fa-142">For more information, see [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md).</span></span> <span data-ttu-id="f82fa-143">適當地加入其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="f82fa-143">Add more servers as appropriate.</span></span>  
  
#### <a name="to-execute-queries-against-several-configuration-targets-at-the-same-time"></a><span data-ttu-id="f82fa-144">若要同時針對數個組態目標執行查詢</span><span class="sxs-lookup"><span data-stu-id="f82fa-144">To execute queries against several configuration targets at the same time</span></span>  
  
-   <span data-ttu-id="f82fa-145">在您建立中央管理伺服器、一個或多個伺服器群組以及一個或多個已註冊的伺服器之後，就可以同時針對整個群組執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f82fa-145">After you create a central management server, one or more server groups, and one or more registered servers, you can execute queries against a whole group at the same time.</span></span> <span data-ttu-id="f82fa-146">如需有關如何同時執行伺服器群組中伺服器之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的詳細資訊，請參閱[同時針對多部伺服器執行陳述式 &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)。</span><span class="sxs-lookup"><span data-stu-id="f82fa-146">For more information about how to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on the servers in a server group at the same time, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82fa-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f82fa-147">See Also</span></span>  
 [<span data-ttu-id="f82fa-148">使用中央管理伺服器管理多部伺服器</span><span class="sxs-lookup"><span data-stu-id="f82fa-148">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
