---
title: 修改 SQL Server Agent Proxy | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f86793a8ddcc6fe8f981d6b367d2178c5a794ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594342"
---
# <a name="modify-a-sql-server-agent-proxy"></a><span data-ttu-id="6b3d7-102">修改 SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="6b3d7-102">Modify a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="6b3d7-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中修改 Agent proxy [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-103">This topic describes how to modify a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6b3d7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6b3d7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6b3d7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6b3d7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6b3d7-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="6b3d7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6b3d7-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6b3d7-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6b3d7-108">**若要使用下列項目修改 SQL Server Agent Proxy：**</span><span class="sxs-lookup"><span data-stu-id="6b3d7-108">**To modify a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="6b3d7-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6b3d7-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6b3d7-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b3d7-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6b3d7-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="6b3d7-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6b3d7-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="6b3d7-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b3d7-113">Agent Proxy 使用認證來儲存 Windows 使用者帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-113">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="6b3d7-114">認證中所指定的使用者，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行的電腦上必須要有「以批次工作登入」的權限。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-114">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b3d7-115">Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-115">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="6b3d7-116">如果 Proxy 不再擁有子系統的存取權，作業步驟就會失效。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-116">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="6b3d7-117">否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會模擬 Proxy 中所指定的使用者，並執行作業步驟。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="6b3d7-118">如果使用者的登入身分可以存取 Proxy，或者使用者隸屬於可存取 Proxy 的角色，該使用者就可以使用作業步驟中的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-118">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6b3d7-119">Security</span><span class="sxs-lookup"><span data-stu-id="6b3d7-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6b3d7-120">權限</span><span class="sxs-lookup"><span data-stu-id="6b3d7-120">Permissions</span></span>  
 <span data-ttu-id="6b3d7-121">只有 **sysadmin** 固定伺服器角色的成員才能建立、修改或刪除 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-121">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6b3d7-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6b3d7-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="6b3d7-123">若要修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="6b3d7-123">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="6b3d7-124">在 **[物件總管]** 中，按一下加號，展開包含要修改之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 帳戶的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account that you want to modify.</span></span>  
  
2.  <span data-ttu-id="6b3d7-125">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="6b3d7-126">按一下加號展開 **[Proxy]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-126">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="6b3d7-127">按一下加號展開 Proxy 的子系統節點 (例如，[ActiveX Script]\*\*\*\*)。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-127">Click the plus sign to expand the subsystem node for the proxy (for example, **ActiveX Script**).</span></span>  
  
5.  <span data-ttu-id="6b3d7-128">以滑鼠右鍵按一下要修改的 Proxy 帳戶，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-128">Right-click the proxy account you want to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="6b3d7-129">在 [ _proxy_name_**proxy 帳戶屬性**] 對話方塊中，視需要對 proxy 帳戶進行變更。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-129">In the _proxy_name_**Proxy Account Properties** dialog box, make changes to the proxy account as necessary.</span></span> <span data-ttu-id="6b3d7-130">如需有關此對話方塊之選項的詳細資訊，請參閱 [建立 SQL Server Agent Proxy](create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-130">For more information on the options in this dialog box, see [Create a SQL Server Agent Proxy](create-a-sql-server-agent-proxy.md).</span></span>  
  
7.  <span data-ttu-id="6b3d7-131">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6b3d7-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b3d7-132">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="6b3d7-133">若要修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="6b3d7-133">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="6b3d7-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6b3d7-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6b3d7-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="6b3d7-137">如需詳細資訊，請參閱[sp_update_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b3d7-137">For more information, see [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).</span></span>  
  
  
