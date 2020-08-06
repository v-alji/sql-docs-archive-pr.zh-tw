---
title: 建立 SQL Server Agent Proxy | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7582aef38d57b15de968d96357e56c1974d733e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598116"
---
# <a name="create-a-sql-server-agent-proxy"></a><span data-ttu-id="9ecc9-102">建立 SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="9ecc9-102">Create a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="9ecc9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立 SQL Server Agent Proxy。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-103">This topic describes how to create a SQL Server Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9ecc9-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 帳戶會定義作業步驟可以在其中執行的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account defines a security context in which a job step can run.</span></span> <span data-ttu-id="9ecc9-105">每個 Proxy 都對應於一個安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-105">Each proxy corresponds to a security credential.</span></span> <span data-ttu-id="9ecc9-106">若要設定特定作業步驟的權限，請建立具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 子系統之必要權限的 Proxy，然後將該 Proxy 指派給作業步驟。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-106">To set permissions for a particular job step, create a proxy that has the required permissions for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent subsystem, and then assign that proxy to the job step.</span></span>  
  
 <span data-ttu-id="9ecc9-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9ecc9-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9ecc9-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9ecc9-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9ecc9-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="9ecc9-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9ecc9-110">安全性</span><span class="sxs-lookup"><span data-stu-id="9ecc9-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9ecc9-111">**若要使用下列項目建立 SQL Server Agent Proxy：**</span><span class="sxs-lookup"><span data-stu-id="9ecc9-111">**To create a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="9ecc9-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ecc9-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9ecc9-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9ecc9-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ecc9-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="9ecc9-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9ecc9-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="9ecc9-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9ecc9-116">在建立 Proxy 之前，如果沒有認證可用，則必須先建立認證。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-116">You must create a credential before you create a proxy if one is not already available.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ecc9-117">Agent Proxy 使用認證來儲存 Windows 使用者帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-117">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="9ecc9-118">認證中所指定的使用者，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行的電腦上必須要有「以批次工作登入」的權限。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-118">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ecc9-119">Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-119">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="9ecc9-120">如果 Proxy 不再擁有子系統的存取權，作業步驟就會失效。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-120">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="9ecc9-121">否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會模擬 Proxy 中所指定的使用者，並執行作業步驟。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-121">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="9ecc9-122">建立 Proxy 並不會改變 Proxy 認證中所指定之使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-122">Creation of a proxy does not change the permissions for the user that is specified in the credential for the proxy.</span></span> <span data-ttu-id="9ecc9-123">例如，您可能會為沒有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之連接權限的使用者建立 Proxy，</span><span class="sxs-lookup"><span data-stu-id="9ecc9-123">For example, you can create a proxy for a user that does not have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ecc9-124">在此情況下，使用該 Proxy 的作業步驟，便無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-124">In this case, job steps that use that proxy are unable to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9ecc9-125">如果使用者的登入身分可以存取 Proxy，或者使用者隸屬於可存取 Proxy 的角色，該使用者就可以使用作業步驟中的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-125">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ecc9-126">Security</span><span class="sxs-lookup"><span data-stu-id="9ecc9-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9ecc9-127">權限</span><span class="sxs-lookup"><span data-stu-id="9ecc9-127">Permissions</span></span>  
  
-   <span data-ttu-id="9ecc9-128">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員才擁有建立、修改或刪除 Proxy 帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-128">Only members of the **sysadmin** fixed server role have permission to create, modify, or delete proxy accounts.</span></span> <span data-ttu-id="9ecc9-129">非 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，必須加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫中的下列其中一個** Agent 固定資料庫角色，才可使用 Proxy： **SQLAgentUserRole**、 **SQLAgentReaderRole**或 **SQLAgentOperatorRole**。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-129">Users who are not members of the **sysadmin** fixed server role must be added to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database to use proxies: **SQLAgentUserRole**, **SQLAgentReaderRole**, or **SQLAgentOperatorRole**.</span></span>  
  
-   <span data-ttu-id="9ecc9-130">如果除了 Proxy 之外還要建立認證，需要 `ALTER ANY CREDENTIAL` 權限。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-130">Requires `ALTER ANY CREDENTIAL` permission if creating a credential in addition to the proxy.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9ecc9-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ecc9-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="9ecc9-132">若要建立 SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="9ecc9-132">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="9ecc9-133">在 **[物件總管]** 中，按一下加號展開要建立 SQL Server Agent Proxy 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-133">In **Object Explorer**, click the plus sign to expand the server where you want to create a proxy on SQL Server Agent.</span></span>  
  
2.  <span data-ttu-id="9ecc9-134">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-134">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9ecc9-135">以滑鼠右鍵按一下 [Proxy]\*\*\*\* 資料夾，然後選取 [新增 Proxy]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-135">Right-click the **Proxies** folder and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="9ecc9-136">在 **[新 Proxy 帳戶]** 對話方塊，於 **[一般]** 頁面上的 **[Proxy 名稱]** 方塊中輸入 Proxy 帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-136">On the **New Proxy Account** dialog box, on the **General** page, enter the name of the proxy account in the **Proxy name** box.</span></span>  
  
5.  <span data-ttu-id="9ecc9-137">在 **[認證名稱]** 方塊中，輸入 Proxy 帳戶將使用之安全性認證的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-137">In the **Credential name** box, enter the name of the security credential that the proxy account will use.</span></span>  
  
6.  <span data-ttu-id="9ecc9-138">在 **[說明]** 方塊中，輸入 Proxy 帳戶的說明。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-138">In the **Description** box, enter a description for the proxy account</span></span>  
  
7.  <span data-ttu-id="9ecc9-139">在 **[對下列子系統有效]** 下，選取此 Proxy 的適當子系統。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-139">Under **Active to the following subsystems**, select the appropriate subsystem or subsystems for this proxy.</span></span>  
  
8.  <span data-ttu-id="9ecc9-140">在 **[主體]** 頁面上，加入或移除登入或角色，藉此授與或移除 Proxy 帳戶的存取。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-140">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
9. <span data-ttu-id="9ecc9-141">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-141">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9ecc9-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9ecc9-142">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="9ecc9-143">若要建立 SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="9ecc9-143">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="9ecc9-144">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ecc9-145">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-145">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9ecc9-146">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9ecc9-146">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 <span data-ttu-id="9ecc9-147">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecc9-147">For more information, see:</span></span>  
  
-   [<span data-ttu-id="9ecc9-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ecc9-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="9ecc9-149">sp_add_proxy &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="9ecc9-149">sp_add_proxy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [<span data-ttu-id="9ecc9-150">sp_grant_proxy_to_subsystem &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="9ecc9-150">sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
