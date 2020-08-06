---
title: 設為主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595358"
---
# <a name="make-a-master-server"></a><span data-ttu-id="e8045-102">設定為主要伺服器</span><span class="sxs-lookup"><span data-stu-id="e8045-102">Make a Master Server</span></span>
  <span data-ttu-id="e8045-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 設為主要伺服器 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8045-103">This topic describes how to make a master server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e8045-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e8045-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e8045-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e8045-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e8045-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e8045-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e8045-107">**若要設為主要伺服器，使用：**</span><span class="sxs-lookup"><span data-stu-id="e8045-107">**To make a master server, using:**</span></span>  
  
     [<span data-ttu-id="e8045-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e8045-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e8045-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e8045-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8045-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="e8045-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8045-111">Security</span><span class="sxs-lookup"><span data-stu-id="e8045-111">Security</span></span>  
 <span data-ttu-id="e8045-112">具有與 Proxy 相關聯之步驟的散發式作業，而該 Proxy 是在目標伺服器上的 Proxy 帳戶內容下執行 。</span><span class="sxs-lookup"><span data-stu-id="e8045-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="e8045-113">請確保符合以下條件，否則與 Proxy 相關聯之作業步驟將不會從主要伺服器下載至目標：</span><span class="sxs-lookup"><span data-stu-id="e8045-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="e8045-114">主伺服器登錄子機碼**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 設定為 1 (true) 。</span><span class="sxs-lookup"><span data-stu-id="e8045-114">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="e8045-115">依預設，這個子機碼設為 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="e8045-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="e8045-116">存在於目標伺服器上的 Proxy 帳戶，而該帳戶名稱與執行作業步驟之主要伺服器上的 Proxy 帳戶名稱相同。</span><span class="sxs-lookup"><span data-stu-id="e8045-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="e8045-117">如果使用 Proxy 帳戶的作業步驟在從主要伺服器下載 Proxy 帳戶至目標伺服器時失敗，您可以在 **msdb** 資料庫的 **sysdownloadlist** 資料表中，檢查 **error_message** 資料行，以了解下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="e8045-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="e8045-118">「作業步驟需要 Proxy 帳戶，不過目標伺服器上已停用 Proxy 比對。」</span><span class="sxs-lookup"><span data-stu-id="e8045-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="e8045-119">若要解決這個錯誤，請將 **AllowDownloadedJobsToMatchProxyName** 登錄子機碼設為 1。</span><span class="sxs-lookup"><span data-stu-id="e8045-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="e8045-120">「找不到 Proxy。」</span><span class="sxs-lookup"><span data-stu-id="e8045-120">"Proxy not found."</span></span>  
  
     <span data-ttu-id="e8045-121">若要解決這個錯誤，請確定目標伺服器上有 Proxy 帳戶，且帳戶名稱與執行該作業步驟的主要伺服器 Proxy 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="e8045-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8045-122">權限</span><span class="sxs-lookup"><span data-stu-id="e8045-122">Permissions</span></span>  
 <span data-ttu-id="e8045-123">這個程序的執行權限預設會授與系統管理員 () 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="e8045-123">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e8045-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e8045-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="e8045-125">若要設為主要伺服器</span><span class="sxs-lookup"><span data-stu-id="e8045-125">To make a master server</span></span>  
  
1.  <span data-ttu-id="e8045-126">在**物件總管中，** 連接到的實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="e8045-126">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e8045-127">以滑鼠右鍵按一下 **[SQL Server Agent]**，指向 **[多重伺服器管理]**，然後按一下 **[設為主要伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="e8045-127">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Master**.</span></span> <span data-ttu-id="e8045-128">**「主要伺服器精靈」** 會引導您完成設定主要伺服器與新增目標伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="e8045-128">The **Master Server Wizard** guides you through the process of making a master server and adding target servers.</span></span>  
  
3.  <span data-ttu-id="e8045-129">從 [主要伺服器操作員]\*\*\*\* 頁面設定主要伺服器的操作員。若要使用電子郵件或呼叫器傳送通知給操作員，則必須設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e8045-129">From the **Master Server Operator** page, configure an operator for the master server To send notifications to operators by using e-mail or pagers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to send e-mail.</span></span> <span data-ttu-id="e8045-130">若要使用 **net send**傳送通知給操作員， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 所在伺服器上必須執行 Messenger 服務。</span><span class="sxs-lookup"><span data-stu-id="e8045-130">To send notifications to operators by using **net send**, the Messenger service must be running on the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resides.</span></span>  
  
     <span data-ttu-id="e8045-131">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="e8045-131">**E-mail address**</span></span>  
     <span data-ttu-id="e8045-132">設定操作員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="e8045-132">Sets the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="e8045-133">**呼叫器號碼**</span><span class="sxs-lookup"><span data-stu-id="e8045-133">**Pager address**</span></span>  
     <span data-ttu-id="e8045-134">設定操作員的呼叫器電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="e8045-134">Sets the pager e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="e8045-135">**Net Send 位址**</span><span class="sxs-lookup"><span data-stu-id="e8045-135">**Net send address**</span></span>  
     <span data-ttu-id="e8045-136">設定操作員的 **net send** 地址。</span><span class="sxs-lookup"><span data-stu-id="e8045-136">Sets the **net send** address for the operator.</span></span>  
  
4.  <span data-ttu-id="e8045-137">從 **[目標伺服器]** 頁面選取主要伺服器的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8045-137">From the **Target Server** page, select target servers for the master server.</span></span>  
  
     <span data-ttu-id="e8045-138">**已註冊的伺服器**</span><span class="sxs-lookup"><span data-stu-id="e8045-138">**Registered Servers**</span></span>  
     <span data-ttu-id="e8045-139">列出在 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 註冊，但尚未成為目標伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8045-139">Lists the servers registered in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] that are not already target servers.</span></span>  
  
     <span data-ttu-id="e8045-140">**目標伺服器**</span><span class="sxs-lookup"><span data-stu-id="e8045-140">**Target Servers**</span></span>  
     <span data-ttu-id="e8045-141">列出目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8045-141">Lists the servers that are target servers.</span></span>  
  
     **>**  
     <span data-ttu-id="e8045-142">將選取的伺服器移動至目標伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="e8045-142">Move the selected server to the target server list.</span></span>  
  
     **>>**  
     <span data-ttu-id="e8045-143">將所有的伺服器移動至目標伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="e8045-143">Move all servers to the target server list.</span></span>  
  
     **<**  
     <span data-ttu-id="e8045-144">將選取的伺服器從目標伺服器清單中移除。</span><span class="sxs-lookup"><span data-stu-id="e8045-144">Remove the selected server from the target server list.</span></span>  
  
     **<<**  
     <span data-ttu-id="e8045-145">將所有的伺服器從目標伺服器清單中移除。</span><span class="sxs-lookup"><span data-stu-id="e8045-145">Remove all servers from the target server list.</span></span>  
  
     <span data-ttu-id="e8045-146">**加入連接**</span><span class="sxs-lookup"><span data-stu-id="e8045-146">**Add connection**</span></span>  
     <span data-ttu-id="e8045-147">將伺服器加入目標伺服器清單中，但不註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8045-147">Add a server to the target server list without registering the server.</span></span>  
  
     <span data-ttu-id="e8045-148">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="e8045-148">**Connection**</span></span>  
     <span data-ttu-id="e8045-149">變更選取之伺服器的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="e8045-149">Change the connection properties for the selected server.</span></span>  
  
5.  <span data-ttu-id="e8045-150">從 **[主要伺服器登入認證]** 頁面指定在必要時，是否要為目標伺服器建立新的登入，並指派存取主要伺服器的權限給該登入。</span><span class="sxs-lookup"><span data-stu-id="e8045-150">From the **Master Server Login Credentials** page to specify if you want to create a new login for the target server, if necessary, and assign it rights to the master server.</span></span>  
  
     <span data-ttu-id="e8045-151">**如有必要，請建立新的登入，並指派存取 MSX 的權限給該登入**</span><span class="sxs-lookup"><span data-stu-id="e8045-151">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="e8045-152">如果指定的登入並不存在，就會在目標伺服器上建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="e8045-152">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e8045-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e8045-153">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="e8045-154">若要設為主要伺服器</span><span class="sxs-lookup"><span data-stu-id="e8045-154">To make a master server</span></span>  
  
1.  <span data-ttu-id="e8045-155">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8045-155">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8045-156">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e8045-156">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8045-157">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e8045-157">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e8045-158">這個範例會將目前的伺服器列入 AdventureWorks1 主要伺服器中。</span><span class="sxs-lookup"><span data-stu-id="e8045-158">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="e8045-159">目前伺服器的位置是「第 21 棟，309 室，機架 5」。</span><span class="sxs-lookup"><span data-stu-id="e8045-159">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 <span data-ttu-id="e8045-160">如需詳細資訊，請參閱[sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e8045-160">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8045-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8045-161">See Also</span></span>  
 <span data-ttu-id="e8045-162">[建立多伺服器環境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="e8045-162">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 [<span data-ttu-id="e8045-163">將整個企業的管理自動化</span><span class="sxs-lookup"><span data-stu-id="e8045-163">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
