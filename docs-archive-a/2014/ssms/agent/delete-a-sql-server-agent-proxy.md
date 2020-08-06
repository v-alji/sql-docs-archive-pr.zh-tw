---
title: 刪除 SQL Server Agent Proxy | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
ms.openlocfilehash: a672c6392e2ffed3ca2a7ed655b806d9d093b10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598112"
---
# <a name="delete-a-sql-server-agent-proxy"></a><span data-ttu-id="7f2d5-102">Delete a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="7f2d5-102">Delete a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="7f2d5-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7f2d5-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7f2d5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7f2d5-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7f2d5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7f2d5-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="7f2d5-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7f2d5-107">安全性</span><span class="sxs-lookup"><span data-stu-id="7f2d5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7f2d5-108">**若要使用下列項目刪除 SQL Server Agent Proxy 帳戶：**</span><span class="sxs-lookup"><span data-stu-id="7f2d5-108">**To delete a SQL Server Agent proxy account, using:**</span></span>  
  
     [<span data-ttu-id="7f2d5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7f2d5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7f2d5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7f2d5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7f2d5-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="7f2d5-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7f2d5-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="7f2d5-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7f2d5-113">當您刪除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 帳戶時，請確定該 Proxy 未參考任何作用中的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-113">When you delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account, make sure the proxy does not reference any active job steps.</span></span> <span data-ttu-id="7f2d5-114">若要檢查是否有任何作業步驟參考該 Proxy，請以滑鼠右鍵按一下該 Proxy，選取 [屬性]\*\*\*\*，然後選取 [<Proxy 名稱> Proxy 帳戶屬性]__\*\*\*\* 對話方塊中的 [參考]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-114">To check for any job steps that reference the proxy, right-click the proxy, select **Properties**, and then, in the _proxy_name_**Proxy Account Properties** dialog box, select the **References** page.</span></span> <span data-ttu-id="7f2d5-115">如果刪除一個 Proxy， **[刪除物件]** 對話方塊中有個選項，可以重新指派該 Proxy 使用的所有作業步驟。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-115">If you delete a proxy, you are given the option to reassign all job steps that use that proxy in the **Delete Object** dialog box.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f2d5-116">Agent Proxy 使用認證來儲存 Windows 使用者帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-116">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="7f2d5-117">認證中所指定的使用者，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行的電腦上必須要有「以批次工作登入」的權限。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-117">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f2d5-118">Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-118">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="7f2d5-119">如果 Proxy 不再擁有子系統的存取權，作業步驟就會失效。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-119">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="7f2d5-120">否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會模擬 Proxy 中所指定的使用者，並執行作業步驟。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-120">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="7f2d5-121">如果使用者的登入身分可以存取 Proxy，或者使用者隸屬於可存取 Proxy 的角色，該使用者就可以使用作業步驟中的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-121">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7f2d5-122">Security</span><span class="sxs-lookup"><span data-stu-id="7f2d5-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7f2d5-123">權限</span><span class="sxs-lookup"><span data-stu-id="7f2d5-123">Permissions</span></span>  
 <span data-ttu-id="7f2d5-124">只有 **sysadmin** 固定伺服器角色的成員才能建立、修改或刪除 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-124">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7f2d5-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7f2d5-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="7f2d5-126">若要刪除 SQL Server Agent Proxy 帳戶</span><span class="sxs-lookup"><span data-stu-id="7f2d5-126">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="7f2d5-127">在 **[物件總管]** 中，按一下加號，展開包含要刪除之 Agent Proxy 帳戶的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-127">In **Object Explorer**, click the plus sign to expand a server that contains the proxy account that you want to delete.</span></span>  
  
2.  <span data-ttu-id="7f2d5-128">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7f2d5-129">按一下加號展開 **[Proxy]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-129">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="7f2d5-130">按一下加號，展開包含要刪除之 Proxy 帳戶的子系統 (例如 [ActiveX Script]\*\*\*\*)。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-130">Click the plus sign to expand the subsystem that contains the proxy account you want to delete (for example, **ActiveX Script)**.</span></span>  
  
5.  <span data-ttu-id="7f2d5-131">以滑鼠右鍵按一下您要刪除的 Proxy 帳戶，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-131">Right-click the proxy account that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="7f2d5-132">在 **[刪除物件]** 對話方塊中，確認已選取正確的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-132">In the **Delete Object** dialog box, confirm that the correct proxy account is selected.</span></span> <span data-ttu-id="7f2d5-133">核取 **[重新指派給]** 核取方塊，將參考此 Proxy 帳戶的工作步驟重新指派給另一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-133">Check the **Reassign to** check box to reassign the job steps that reference this proxy account to another account.</span></span>  
  
7.  <span data-ttu-id="7f2d5-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7f2d5-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7f2d5-135">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="7f2d5-136">若要刪除 SQL Server Agent Proxy 帳戶</span><span class="sxs-lookup"><span data-stu-id="7f2d5-136">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="7f2d5-137">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7f2d5-138">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7f2d5-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 <span data-ttu-id="7f2d5-140">如需詳細資訊，請參閱[sp_delete_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7f2d5-140">For more information, see [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).</span></span>  
  
  
