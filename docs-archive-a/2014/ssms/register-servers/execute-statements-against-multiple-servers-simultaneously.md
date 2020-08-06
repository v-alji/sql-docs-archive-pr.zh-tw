---
title: 同時對多部伺服器執行陳述式
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b94775029a1501d3e894d84ef4a027fc1595dc10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702269"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a><span data-ttu-id="03285-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="03285-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span></span>
  <span data-ttu-id="03285-103">本主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，透過建立本機伺服器群組或中央管理伺服器及一個或多個伺服器群組，以及位於這些群組內部的一個或多個已註冊的伺服器，然後查詢完整的群組的方式，同時查詢多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="03285-103">This topic describes how to query multiple servers at the same time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by creating a local server group, or a Central Management Server and one or more server groups, and one or more registered servers within the groups, and then querying the complete group.</span></span> <span data-ttu-id="03285-104">此查詢傳回的結果可以結合到單一結果窗格中，也可以在不同的結果窗格中傳回。</span><span class="sxs-lookup"><span data-stu-id="03285-104">The results that are returned by the query can be combined into a single results pane, or can be returned in separate results panes.</span></span> <span data-ttu-id="03285-105">結果集可能包括伺服器名稱以及查詢在每部伺服器上使用之登入的額外資料行。</span><span class="sxs-lookup"><span data-stu-id="03285-105">The results set can include additional columns for the server name and the login that is used by the query on each server.</span></span> <span data-ttu-id="03285-106">中央管理伺服器和從屬伺服器可以使用 Windows 驗證來註冊。</span><span class="sxs-lookup"><span data-stu-id="03285-106">Central Management Servers and subordinate servers can be registered by using only Windows Authentication.</span></span> <span data-ttu-id="03285-107">本機伺服器群組中的伺服器則可以使用 Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行註冊。</span><span class="sxs-lookup"><span data-stu-id="03285-107">Servers in local server groups can be registered by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03285-108">在您執行下列程序之前，請先建立中央管理伺服器和伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="03285-108">Before you execute the following procedures, create a Central Management Server and server groups.</span></span> <span data-ttu-id="03285-109">如需詳細資訊，請參閱[建立中央管理伺服器和伺服器群組 &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)。</span><span class="sxs-lookup"><span data-stu-id="03285-109">For more information, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).</span></span>  
  
 <span data-ttu-id="03285-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="03285-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="03285-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="03285-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="03285-112">安全性</span><span class="sxs-lookup"><span data-stu-id="03285-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="03285-113">**若要對多部伺服器執行陳述式，使用：**</span><span class="sxs-lookup"><span data-stu-id="03285-113">**To execute statements against multiple servers, using:**</span></span>  
  
     [<span data-ttu-id="03285-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="03285-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="03285-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="03285-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="03285-116">Security</span><span class="sxs-lookup"><span data-stu-id="03285-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="03285-117">權限</span><span class="sxs-lookup"><span data-stu-id="03285-117">Permissions</span></span>  
 <span data-ttu-id="03285-118">由於中央管理伺服器所維護的連接會在使用者的內容中執行，所以使用 Windows 驗證時，已註冊之伺服器上的有效權限可能會不同。</span><span class="sxs-lookup"><span data-stu-id="03285-118">Because the connections maintained by a Central Management Server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="03285-119">例如，雖然使用者可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員，但是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 執行個體上具有有限的權限。</span><span class="sxs-lookup"><span data-stu-id="03285-119">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="03285-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="03285-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a><span data-ttu-id="03285-121">同時針對多個組態目標執行陳述式</span><span class="sxs-lookup"><span data-stu-id="03285-121">To execute statements against multiple configuration targets simultaneously</span></span>  
  
1.  <span data-ttu-id="03285-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **[檢視]** 功能表中，按一下 **[已註冊的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="03285-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="03285-123">展開中央管理伺服器，以滑鼠右鍵按一下伺服器群組，指向 [連接]\*\*\*\*，然後按一下 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03285-123">Expand a Central Management Server, right-click a server group, point to **Connect**, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="03285-124">在 [查詢編輯器] 中，輸入並執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，例如下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="03285-124">In Query Editor, type and execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as the following:</span></span>  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     <span data-ttu-id="03285-125">根據預設，結果窗格將會結合伺服器群組中所有伺服器的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="03285-125">By default, the results pane will combine the query results from all the servers in the server group.</span></span>  
  
#### <a name="to-change-the-multiserver-results-options"></a><span data-ttu-id="03285-126">變更多伺服器結果選項</span><span class="sxs-lookup"><span data-stu-id="03285-126">To change the multiserver results options</span></span>  
  
1.  <span data-ttu-id="03285-127">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="03285-127">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="03285-128">展開 **[查詢結果]**、展開 **[SQL Server]**，然後按一下 **[多伺服器結果]**。</span><span class="sxs-lookup"><span data-stu-id="03285-128">Expand **Query Results**, expand **SQL Server**, and then click **Multiserver Results**.</span></span>  
  
3.  <span data-ttu-id="03285-129">在 **[多伺服器結果]** 頁面上，指定您想要的選項設定，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="03285-129">On the **Multiserver Results** page, specify the option settings that you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03285-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03285-130">See Also</span></span>  
 [<span data-ttu-id="03285-131">使用中央管理伺服器管理多部伺服器</span><span class="sxs-lookup"><span data-stu-id="03285-131">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
