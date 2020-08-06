---
title: 設為目標伺服器| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.tsxwiz.msx.f1
- sql12.ag.tsxwiz.cover.f1
- sql12.ag.tsxwiz.credentials.f1
- sql12.ag.tsxwiz.complete.f1
helpviewer_keywords:
- Target Server Wizard
- SQL Server Agent jobs, target servers
- target servers [SQL Server], creating
ms.assetid: 13aabe2d-67fe-4c67-8d49-2928dd705b7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd60a19234d186bb0912978589fa60fd8e8a8c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686756"
---
# <a name="make-a-target-server"></a><span data-ttu-id="dd3f7-102">設為目標伺服器</span><span class="sxs-lookup"><span data-stu-id="dd3f7-102">Make a Target Server</span></span>
  <span data-ttu-id="dd3f7-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 管理物件 (SMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中設定目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-103">This topic describes how to make a target server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="dd3f7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dd3f7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dd3f7-106">安全性</span><span class="sxs-lookup"><span data-stu-id="dd3f7-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dd3f7-107">**若要設定目標伺服器，使用：**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-107">**To make a target server, using:**</span></span>  
  
     [<span data-ttu-id="dd3f7-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dd3f7-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dd3f7-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dd3f7-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="dd3f7-110">SMO</span><span class="sxs-lookup"><span data-stu-id="dd3f7-110">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dd3f7-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="dd3f7-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dd3f7-112">Security</span><span class="sxs-lookup"><span data-stu-id="dd3f7-112">Security</span></span>  
 <span data-ttu-id="dd3f7-113">具有與 Proxy 相關聯之步驟的散發式作業，而該 Proxy 是在目標伺服器上的 Proxy 帳戶內容下執行 。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-113">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="dd3f7-114">請確保符合以下條件，否則與 Proxy 相關聯之作業步驟將不會從主要伺服器下載至目標：</span><span class="sxs-lookup"><span data-stu-id="dd3f7-114">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="dd3f7-115">主伺服器登錄子機碼**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 設定為 1 (true) 。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-115">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="dd3f7-116">依預設，這個子機碼設為 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-116">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="dd3f7-117">存在於目標伺服器上的 Proxy 帳戶，而該帳戶名稱與執行作業步驟之主要伺服器上的 Proxy 帳戶名稱相同。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-117">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="dd3f7-118">如果使用 Proxy 帳戶的作業步驟在從主要伺服器下載 Proxy 帳戶至目標伺服器時失敗，您可以在 **msdb** 資料庫的 **sysdownloadlist** 資料表中，檢查 **error_message** 資料行，以了解下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="dd3f7-118">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="dd3f7-119">「作業步驟需要 Proxy 帳戶，不過目標伺服器上已停用 Proxy 比對。」</span><span class="sxs-lookup"><span data-stu-id="dd3f7-119">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="dd3f7-120">若要解決這個錯誤，請將 **AllowDownloadedJobsToMatchProxyName** 登錄子機碼設為 1。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-120">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="dd3f7-121">「找不到 Proxy。」</span><span class="sxs-lookup"><span data-stu-id="dd3f7-121">"Proxy not found."</span></span>  
  
     <span data-ttu-id="dd3f7-122">若要解決這個錯誤，請確定目標伺服器上有 Proxy 帳戶，且帳戶名稱與執行該作業步驟的主要伺服器 Proxy 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-122">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dd3f7-123">權限</span><span class="sxs-lookup"><span data-stu-id="dd3f7-123">Permissions</span></span>  
 <span data-ttu-id="dd3f7-124">這個程序的執行權限預設會授與系統管理員 () 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-124">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dd3f7-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dd3f7-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="dd3f7-126">若要設為目標伺服器</span><span class="sxs-lookup"><span data-stu-id="dd3f7-126">To make a target server</span></span>  
  
1.  <span data-ttu-id="dd3f7-127">在**物件總管中，** 連接到的實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-127">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="dd3f7-128">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*、指向 [多重伺服器管理]\*\*\*\*，然後按一下 [設為目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-128">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Target**.</span></span> <span data-ttu-id="dd3f7-129">**[目標伺服器精靈]** 將引導您執行將此伺服器設定為目標伺服器的程序。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-129">The **Target Server Wizard** guides you through the process of making a target server.</span></span>  
  
3.  <span data-ttu-id="dd3f7-130">從 **[選取主要伺服器]** 頁面選取此目標伺服器將接收作業來源的主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-130">From the **Select a Master Server** page, select the master server that this target server will receive jobs from.</span></span>  
  
     <span data-ttu-id="dd3f7-131">**挑選伺服器**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-131">**Pick Server**</span></span>  
     <span data-ttu-id="dd3f7-132">連接到主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-132">Connect to the master server.</span></span>  
  
     <span data-ttu-id="dd3f7-133">**此伺服器的描述**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-133">**Description of this server**</span></span>  
     <span data-ttu-id="dd3f7-134">鍵入此目標伺服器的描述。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-134">Type a description for this target server.</span></span> <span data-ttu-id="dd3f7-135">目標伺服器會將此描述上傳至主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-135">The target server uploads this description to the master server.</span></span>  
  
4.  <span data-ttu-id="dd3f7-136">從 **[主要伺服器登入認證]** 頁面建立目標伺服器上的新登入 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-136">From the **Master Server Login Credentials** page, create a new login on the target server, if necessary.</span></span>  
  
     <span data-ttu-id="dd3f7-137">**如有必要，請建立新的登入，並指派存取 MSX 的權限給該登入**</span><span class="sxs-lookup"><span data-stu-id="dd3f7-137">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="dd3f7-138">如果指定的登入並不存在，就會在目標伺服器上建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-138">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dd3f7-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dd3f7-139">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="dd3f7-140">若要設為目標伺服器</span><span class="sxs-lookup"><span data-stu-id="dd3f7-140">To make a target server</span></span>  
  
1.  <span data-ttu-id="dd3f7-141">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dd3f7-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dd3f7-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="dd3f7-144">這個範例會將目前的伺服器列入 AdventureWorks1 主要伺服器中。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-144">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="dd3f7-145">目前伺服器的位置是「第 21 棟，309 室，機架 5」。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-145">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
        N'Building 21, Room 309, Rack 5' ;   
    GO;  
    ```  
  
     <span data-ttu-id="dd3f7-146">如需詳細資訊，請參閱[sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dd3f7-146">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="dd3f7-147">使用 SQL Server 管理物件 (SMO) </span><span class="sxs-lookup"><span data-stu-id="dd3f7-147">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3f7-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd3f7-148">See Also</span></span>  
 [<span data-ttu-id="dd3f7-149">將整個企業的管理自動化</span><span class="sxs-lookup"><span data-stu-id="dd3f7-149">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
