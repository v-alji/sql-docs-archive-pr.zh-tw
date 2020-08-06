---
title: 設定 Database Mail | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Sql12.swb.sqlimail.newaccount.f1
- Sql12.swb.sqlimail.manageexistingaccount.f1
- Sql12.swb.dbmail.manageexistingaccount.f1
- Sql12.swb.sqlimail.manageexistingprofile.f1
- Sql12.swb.sqlimail.newprofile.f1
- Sql12.swb.sqlimail.profileandaccountmanagement.f1
- Sql12.swb.dbmail.configuresystem.f1
- Sql12.swb.dbmail.profileandaccountmanagement.f1
- Sql12.swb.dbmail. manageprofilesecurity.profileview.f1
- Sql12.swb.dbmail.selectconfiguration.f1
- Sql12.swb.dbmail.newsqlimailaccount.f1
- Sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- Sql12.swb.sqlimail.newsqlimailaccount.f1
- Sql12.swb.dbmail.newaccount.f1
- Sql12.swb.dbmail.manageexistingprofile.f1
- Sql12.swb.sqlimail.configuresystem.f1
- Sql12.swb.sqlimail.selectconfiguration.f1
- Sql12.swb.dbmail.completewizard.f1
- Sql12.swb.sqlimail.welcome.f1
- sql12.swb.dbmail.sendtestemail.f1
- Sql12.swb.sqlimail.addaccounttoprofile.f1
- Sql12.swb.dbmail.welcome.f1
- Sql12.swb.dbmail.newprofile.f1
- Sql12.swb.dbmail.addaccounttoprofile.f1
- sql12.swb.dbmail.sendtestemail.test.f1
- Sql12.swb.sqlimail.completewizard.f1
- Sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- Sql12.swb.dbmail.manageprofilesecurity.principalview.f1
ms.assetid: 7edc21d4-ccf3-42a9-84c0-3f70333efce6
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbf9af4b5af3043c6ca8fa2cba01ebe43019fb41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606873"
---
# <a name="configure-database-mail"></a><span data-ttu-id="8743b-102">設定 Database Mail</span><span class="sxs-lookup"><span data-stu-id="8743b-102">Configure Database Mail</span></span>
  <span data-ttu-id="8743b-103">本主題說明如何使用 Database Mail 組態精靈來啟用及設定 Database Mail，並使用範本建立 Database Mail 組態指令碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-103">This topic describes how to enable and configure Database Mail using the Database Mail Configuration Wizard, and create a Database Mail Configuration script using templates.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8743b-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="8743b-104">Before You Begin</span></span>  
 <span data-ttu-id="8743b-105">使用 [DatabaseMail XP] 選項，可在此伺服器上啟用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8743b-105">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="8743b-106">如需詳細資訊，請參閱 [Database Mail XPs 伺服器組態選項](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 參考主題。</span><span class="sxs-lookup"><span data-stu-id="8743b-106">For more information, see [Database Mail XPs Server Configuration Option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) reference topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8743b-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="8743b-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8743b-108">在任何資料庫中啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker 都需要資料庫鎖定。</span><span class="sxs-lookup"><span data-stu-id="8743b-108">Enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker in any database requires a database lock.</span></span> <span data-ttu-id="8743b-109">如果已在 **msdb**中停用 Service Broker，則啟用 Database Mail 的第一步是停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent，好讓 Service Broker 可以取得必要的鎖定。</span><span class="sxs-lookup"><span data-stu-id="8743b-109">If Service Broker was deactivated in **msdb**, to enable Database Mail, first stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent so Service Broker can obtain the necessary lock.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8743b-110">Security</span><span class="sxs-lookup"><span data-stu-id="8743b-110">Security</span></span>  
 <span data-ttu-id="8743b-111">若要設定 Database Mail，您必須是 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="8743b-111">To configure Database Mail you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="8743b-112">若要傳送 Database Mail，您必須是 **msdb** 資料庫之 **DatabaseMailUserRole** 資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="8743b-112">To send Database Mail you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8743b-113">使用 Database Mail 組態精靈</span><span class="sxs-lookup"><span data-stu-id="8743b-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="8743b-114">**若要使用精靈設定 Database Mail**</span><span class="sxs-lookup"><span data-stu-id="8743b-114">**To configure Database Mail using a wizard**</span></span>  
  
1.  <span data-ttu-id="8743b-115">在物件總管中，展開您想要設定 Database Mail 之執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="8743b-115">In Object Explorer, expand the node for the instance  you want to configure Database mail.</span></span>  
  
2.  <span data-ttu-id="8743b-116">展開 [**管理**] 節點。</span><span class="sxs-lookup"><span data-stu-id="8743b-116">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="8743b-117">以滑鼠右鍵按一下 [Database Mail]\*\*\*\*，然後按一下 [設定 Database Mail]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8743b-117">Right-click **Database Mail**, and then click **Configure Database Mail**.</span></span>  
  
4.  <span data-ttu-id="8743b-118">完成精靈對話方塊</span><span class="sxs-lookup"><span data-stu-id="8743b-118">Complete the Wizard dialogs</span></span>  
  

  
  
  
###  <a name="welcome-page"></a><a name="Welcome"></a><span data-ttu-id="8743b-119">歡迎頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-119">Welcome Page</span></span>  
 <span data-ttu-id="8743b-120">此頁說明設定 Database Mail 的步驟。</span><span class="sxs-lookup"><span data-stu-id="8743b-120">This page describes the steps to configuring Database Mail.</span></span>  
  
 <span data-ttu-id="8743b-121">**不要再顯示此頁面**-核取此選項可略過此歡迎頁面，而不會在未來顯示。</span><span class="sxs-lookup"><span data-stu-id="8743b-121">**Do not show this page again** - Check this to skip this welcome page from displaying in the future.</span></span>  
  
 <span data-ttu-id="8743b-122">**下一步** - 繼續 [選取組態工作]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="8743b-122">**Next** - Proceeds to the **Select a configuration task** page.</span></span>  
  
 <span data-ttu-id="8743b-123">**取消**-結束嚮導而不設定 Database Mail</span><span class="sxs-lookup"><span data-stu-id="8743b-123">**Cancel** - Terminates the wizard without configuring Database Mail</span></span>  
  
 
  
###  <a name="select-configuration-task"></a><a name="ConfigTask"></a><span data-ttu-id="8743b-124">選取設定工作</span><span class="sxs-lookup"><span data-stu-id="8743b-124">Select Configuration Task</span></span>  
 <span data-ttu-id="8743b-125">使用 [選取組態工作]\*\*\*\* 頁面可指出您每次使用精靈時，會完成哪個工作。</span><span class="sxs-lookup"><span data-stu-id="8743b-125">Use the **Select Configuration Task** page, to indicate which task you will complete each time you use the wizard.</span></span> <span data-ttu-id="8743b-126">如果您在完成精靈之前變更了主意，請使用 [上一步]\*\*\*\* 按鈕回到此頁面，然後選取不同的工作。</span><span class="sxs-lookup"><span data-stu-id="8743b-126">If you change your mind before you complete the wizard, use the **Back** button to return to this page and select a different task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8743b-127">如果尚未啟用 Database Mail，您就會接收到訊息： **[無法使用 Database Mail 功能。您要啟用此功能嗎?]**</span><span class="sxs-lookup"><span data-stu-id="8743b-127">If Database Mail has not been enabled, you will receive the message: **The Database Mail feature is not available.  Would you like to enable this feature?**</span></span> <span data-ttu-id="8743b-128">回應 [是]\*\*\*\* 就相當於使用 **sp_configure** 系統預存程序的 [Database Mail XP 選項](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)來啟用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8743b-128">Responding **Yes**, is equivalent to enabling Database Mail by using the [Database Mail XPs option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) of the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="8743b-129">**執行下列工作來設定 Database Mail**</span><span class="sxs-lookup"><span data-stu-id="8743b-129">**Set up Database Mail by performing the following tasks**</span></span>  
 <span data-ttu-id="8743b-130">執行第一次設定 Database Mail 所需的所有工作。</span><span class="sxs-lookup"><span data-stu-id="8743b-130">Perform all of the tasks required to set up Database Mail for the first time.</span></span> <span data-ttu-id="8743b-131">此選項包含所有其他三個選項。</span><span class="sxs-lookup"><span data-stu-id="8743b-131">This option includes all of the other three options.</span></span>  
  
 <span data-ttu-id="8743b-132">**管理 Database Mail 帳戶和設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-132">**Manage Database Mail accounts and profiles**</span></span>  
 <span data-ttu-id="8743b-133">建立新的 Database Mail 帳戶和設定檔，或是檢視、變更或刪除現有的 Database Mail 帳戶和設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-133">Create new Database Mail accounts and profiles or to view, change, or delete existing Database Mail accounts and profiles.</span></span>  
  
 <span data-ttu-id="8743b-134">**管理設定檔安全性**</span><span class="sxs-lookup"><span data-stu-id="8743b-134">**Manage profile security**</span></span>  
 <span data-ttu-id="8743b-135">設定哪些使用者才能夠存取 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-135">Configure which users have access to Database Mail profiles.</span></span>  
  
 <span data-ttu-id="8743b-136">**檢視或變更系統參數**</span><span class="sxs-lookup"><span data-stu-id="8743b-136">**View or change system parameters**</span></span>  
 <span data-ttu-id="8743b-137">設定 Database Mail 系統參數，例如附件的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="8743b-137">Configure Database Mail system parameters such as the maximum file size for attachments.</span></span>  
  

  
###  <a name="new-account-page"></a><a name="NewAccount"></a><span data-ttu-id="8743b-138">[新增帳戶] 頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-138">New Account Page</span></span>  
 <span data-ttu-id="8743b-139">使用這個頁面建立新的 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-139">Use this page to create a new Database Mail account.</span></span> <span data-ttu-id="8743b-140">Database Mail 帳戶包含傳送電子郵件到 SMTP 伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="8743b-140">A Database Mail account contains information for sending e-mail to an SMTP server.</span></span>  
  
 <span data-ttu-id="8743b-141">Database Mail 帳戶包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用來傳送電子郵件訊息到 SMTP 伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="8743b-141">A Database Mail account contains the information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="8743b-142">每個帳戶包含一個電子郵件伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="8743b-142">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="8743b-143">Database Mail 帳戶僅供 Database Mail 使用。</span><span class="sxs-lookup"><span data-stu-id="8743b-143">A Database Mail account is only used for Database Mail.</span></span> <span data-ttu-id="8743b-144">Database Mail 帳戶不會對應至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶或 Microsoft Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-144">A Database Mail account does not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account or a Microsoft Windows account.</span></span> <span data-ttu-id="8743b-145">Database Mail 可以使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的認證、使用您提供的其他認證或以匿名方式傳送。</span><span class="sxs-lookup"><span data-stu-id="8743b-145">Database Mail can be sent using the credentials of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], using other credentials that you supply, or anonymously.</span></span> <span data-ttu-id="8743b-146">使用基本驗證時，Database Mail 帳戶中的名稱和密碼僅用於電子郵件伺服器的驗證。</span><span class="sxs-lookup"><span data-stu-id="8743b-146">When using basic authentication, the user name and password in a Database Mail account are only used for authentication with the e-mail server.</span></span> <span data-ttu-id="8743b-147">帳戶不需要對應到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者，或在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之電腦上的使用者。</span><span class="sxs-lookup"><span data-stu-id="8743b-147">An account need not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user or a user on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8743b-148">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-148">**Account name**</span></span>  
 <span data-ttu-id="8743b-149">輸入新帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-149">Type the name of the new account.</span></span>  
  
 <span data-ttu-id="8743b-150">**說明**</span><span class="sxs-lookup"><span data-stu-id="8743b-150">**Description**</span></span>  
 <span data-ttu-id="8743b-151">輸入帳戶的描述。</span><span class="sxs-lookup"><span data-stu-id="8743b-151">Type a description of the account.</span></span> <span data-ttu-id="8743b-152">描述是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-152">The description is optional.</span></span>  
  
 <span data-ttu-id="8743b-153">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="8743b-153">**E-mail address**</span></span>  
 <span data-ttu-id="8743b-154">鍵入帳戶電子郵件地址的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-154">Type the name of the e-mail address for the account.</span></span> <span data-ttu-id="8743b-155">這是電子郵件傳送來自的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-155">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="8743b-156">例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的帳戶可能會從 SqlAgent@Adventure-Works.com。</span><span class="sxs-lookup"><span data-stu-id="8743b-156">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may send e-mail from the address SqlAgent@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="8743b-157">**顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-157">**Display name**</span></span>  
 <span data-ttu-id="8743b-158">鍵入顯示於由這個帳戶傳送之電子郵件訊息上的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-158">Type the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="8743b-159">顯示名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-159">The display name is optional.</span></span> <span data-ttu-id="8743b-160">這是顯示於由這個帳戶傳送之訊息上的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-160">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="8743b-161">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的帳戶在電子郵件訊息上顯示的名稱可能會是「SQL Server Agent Automated Mailer」。</span><span class="sxs-lookup"><span data-stu-id="8743b-161">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may display the name "SQL Server Agent Automated Mailer" on e-mail messages.</span></span>  
  
 <span data-ttu-id="8743b-162">**回覆電子郵件**</span><span class="sxs-lookup"><span data-stu-id="8743b-162">**Reply e-mail**</span></span>  
 <span data-ttu-id="8743b-163">鍵入將用來回覆給由這個帳戶傳送之電子郵件訊息的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-163">Type the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="8743b-164">回覆電子郵件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-164">The reply e-mail is optional.</span></span> <span data-ttu-id="8743b-165">例如，回覆給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 帳戶的郵件，可能會傳送給資料庫管理員 danw@Adventure-Works.com。</span><span class="sxs-lookup"><span data-stu-id="8743b-165">For example, replies to an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may go to the database administrator, danw@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="8743b-166">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-166">**Server name**</span></span>  
 <span data-ttu-id="8743b-167">輸入帳戶用來傳送電子郵件的 SMTP 伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8743b-167">Type the name or IP address of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="8743b-168">通常這種格式類似于 `smtp.` *<your_company>* `.com` 。</span><span class="sxs-lookup"><span data-stu-id="8743b-168">Typically this is in a format similar to `smtp.`*<your_company>*`.com`.</span></span> <span data-ttu-id="8743b-169">如需相關說明，請洽詢您的郵件管理員。</span><span class="sxs-lookup"><span data-stu-id="8743b-169">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="8743b-170">**連接埠號碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-170">**Port number**</span></span>  
 <span data-ttu-id="8743b-171">輸入此帳戶之 SMTP 伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8743b-171">Type the port number of the SMTP server for this account.</span></span> <span data-ttu-id="8743b-172">多數的 SMTP 伺服器使用通訊埠 25。</span><span class="sxs-lookup"><span data-stu-id="8743b-172">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="8743b-173">**這個伺服器需要安全連接 (SSL)**</span><span class="sxs-lookup"><span data-stu-id="8743b-173">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="8743b-174">使用安全通訊端層 (SSL) 將通訊加密。</span><span class="sxs-lookup"><span data-stu-id="8743b-174">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="8743b-175">**使用 Database Engine 服務認證的 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-175">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="8743b-176">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務設定的認證，來建立 SMTP 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="8743b-176">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8743b-177">**基本驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-177">**Basic Authentication**</span></span>  
 <span data-ttu-id="8743b-178">指定 SMTP 伺服器所需的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-178">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="8743b-179">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-179">**User name**</span></span>  
 <span data-ttu-id="8743b-180">鍵入 Database Mail 用來登入 SMTP 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-180">Type the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8743b-181">如果 SMTP 伺服器需要基本驗證，則使用者名稱是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-181">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-182">**密碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-182">**Password**</span></span>  
 <span data-ttu-id="8743b-183">鍵入 Database Mail 用來登入 SMTP 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-183">Type the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8743b-184">如果 SMTP 伺服器需要基本驗證，則密碼是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-184">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-185">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-185">**Confirm password**</span></span>  
 <span data-ttu-id="8743b-186">再次輸入密碼，以便確認密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-186">Type the password again to confirm the password.</span></span> <span data-ttu-id="8743b-187">如果 SMTP 伺服器需要基本驗證，則密碼是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-187">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-188">**匿名驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-188">**Anonymous authentication**</span></span>  
 <span data-ttu-id="8743b-189">郵件傳送到 SMTP 伺服器時，不使用登入認證。</span><span class="sxs-lookup"><span data-stu-id="8743b-189">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="8743b-190">當 SMTP 伺服器不需要驗證時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8743b-190">Use this option when the SMTP server does not require authentication.</span></span>  
  
 
  
###  <a name="manage-existing-account-page"></a><a name="ExistingAccount"></a><span data-ttu-id="8743b-191">[管理現有帳戶] 頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-191">Manage Existing Account Page</span></span>  
 <span data-ttu-id="8743b-192">使用此頁面來管理現有的 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-192">Use this page to manage an existing Database Mail account.</span></span>  
  
 <span data-ttu-id="8743b-193">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-193">**Account name**</span></span>  
 <span data-ttu-id="8743b-194">選取要檢視、更新或刪除的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-194">Select the account to view, update or delete.</span></span>  
  
 <span data-ttu-id="8743b-195">**刪除**</span><span class="sxs-lookup"><span data-stu-id="8743b-195">**Delete**</span></span>  
 <span data-ttu-id="8743b-196">刪除選取的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-196">Delete the selected account.</span></span> <span data-ttu-id="8743b-197">您必須從相關聯的設定檔移除這個帳戶，或先刪除相關聯的設定檔，再刪除選取的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-197">You must remove this account from associated profiles, or delete such profiles, before you delete the selected account.</span></span>  
  
 <span data-ttu-id="8743b-198">**說明**</span><span class="sxs-lookup"><span data-stu-id="8743b-198">**Description**</span></span>  
 <span data-ttu-id="8743b-199">檢視或更新帳戶的描述。</span><span class="sxs-lookup"><span data-stu-id="8743b-199">View or update the description of the account.</span></span> <span data-ttu-id="8743b-200">描述是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-200">The description is optional.</span></span>  
  
 <span data-ttu-id="8743b-201">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="8743b-201">**E-mail address**</span></span>  
 <span data-ttu-id="8743b-202">檢視或更新帳戶之電子郵件地址的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-202">View or update the name of the e-mail address for the account.</span></span> <span data-ttu-id="8743b-203">這是電子郵件傳送來自的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-203">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="8743b-204">例如，Microsoft SQL Server 代理程式的帳戶可能會從位址傳送電子郵件 **SqlAgent@Adventure-Works.com** 。</span><span class="sxs-lookup"><span data-stu-id="8743b-204">For example, an account for Microsoft SQL Server Agent may send e-mail from the address **SqlAgent@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="8743b-205">**顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-205">**Display name**</span></span>  
 <span data-ttu-id="8743b-206">檢視或更新名稱，以顯示在由這個帳戶傳送的電子郵件訊息上。</span><span class="sxs-lookup"><span data-stu-id="8743b-206">View or update the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="8743b-207">顯示名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-207">The display name is optional.</span></span> <span data-ttu-id="8743b-208">這是顯示於由這個帳戶傳送之訊息上的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-208">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="8743b-209">例如，SQL Server Agent 的帳戶在電子郵件訊息上顯示的名稱可能會是 **SQL Server Agent Automated Mailer** 。</span><span class="sxs-lookup"><span data-stu-id="8743b-209">For example, an account for SQL Server Agent may display the name **SQL Server Agent Automated Mailer** on e-mail messages.</span></span>  
  
 <span data-ttu-id="8743b-210">**回覆電子郵件**</span><span class="sxs-lookup"><span data-stu-id="8743b-210">**Reply e-mail**</span></span>  
 <span data-ttu-id="8743b-211">檢視或更新電子郵件地址，這將用於回覆給由這個帳戶傳送的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="8743b-211">View or update the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="8743b-212">回覆電子郵件是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-212">The reply e-mail is optional.</span></span> <span data-ttu-id="8743b-213">例如，回復 SQL Server Agent 的帳戶可能會前往資料庫管理員 **danw@Adventure-Works.com** 。</span><span class="sxs-lookup"><span data-stu-id="8743b-213">For example, replies to an account for SQL Server Agent may go to the database administrator, **danw@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="8743b-214">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-214">**Server name**</span></span>  
 <span data-ttu-id="8743b-215">檢視或更新帳戶用來傳送電子郵件的 SMTP 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-215">View or update the name of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="8743b-216">一般而言，此格式類似於 **smtp.<貴公司>.com**。</span><span class="sxs-lookup"><span data-stu-id="8743b-216">Typically this is in a format similar to **smtp.<your_company>.com**.</span></span> <span data-ttu-id="8743b-217">如需相關說明，請洽詢您的郵件管理員。</span><span class="sxs-lookup"><span data-stu-id="8743b-217">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="8743b-218">**連接埠號碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-218">**Port number**</span></span>  
 <span data-ttu-id="8743b-219">檢視或更新此帳戶的 SMTP 伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8743b-219">View or update the port number of the SMTP server for this account.</span></span> <span data-ttu-id="8743b-220">多數的 SMTP 伺服器使用通訊埠 25。</span><span class="sxs-lookup"><span data-stu-id="8743b-220">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="8743b-221">**這個伺服器需要安全連接 (SSL)**</span><span class="sxs-lookup"><span data-stu-id="8743b-221">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="8743b-222">使用安全通訊端層 (SSL) 將通訊加密。</span><span class="sxs-lookup"><span data-stu-id="8743b-222">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="8743b-223">**使用 Database Engine 服務認證的 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-223">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="8743b-224">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務設定的認證，來建立 SMTP 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="8743b-224">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8743b-225">**基本驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-225">**Basic Authentication**</span></span>  
 <span data-ttu-id="8743b-226">指定 SMTP 伺服器所需的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-226">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="8743b-227">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-227">**User name**</span></span>  
 <span data-ttu-id="8743b-228">檢視或更新 Database Mail 用來登入 SMTP 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-228">View or update the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8743b-229">如果 SMTP 伺服器需要基本驗證，則使用者名稱是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-229">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-230">**密碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-230">**Password**</span></span>  
 <span data-ttu-id="8743b-231">變更 Database Mail 用來登入 SMTP 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-231">Change the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8743b-232">如果 SMTP 伺服器需要基本驗證，則密碼是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-232">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-233">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-233">**Confirm password**</span></span>  
 <span data-ttu-id="8743b-234">再次輸入密碼，以便確認密碼。</span><span class="sxs-lookup"><span data-stu-id="8743b-234">Type the password again to confirm the password.</span></span> <span data-ttu-id="8743b-235">如果 SMTP 伺服器需要基本驗證，則密碼是必要的。</span><span class="sxs-lookup"><span data-stu-id="8743b-235">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8743b-236">**匿名驗證**</span><span class="sxs-lookup"><span data-stu-id="8743b-236">**Anonymous authentication**</span></span>  
 <span data-ttu-id="8743b-237">郵件傳送到 SMTP 伺服器時，不使用登入認證。</span><span class="sxs-lookup"><span data-stu-id="8743b-237">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="8743b-238">當 SMTP 伺服器不需要驗證時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8743b-238">Use this option when the SMTP server does not require authentication.</span></span>  
  

  
###  <a name="new-profile-page"></a><a name="NewProfile"></a> <span data-ttu-id="8743b-239">新增設定檔頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-239">New Profile Page</span></span>  
 <span data-ttu-id="8743b-240">使用此頁面可建立 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-240">Use this page to create a Database Mail profile.</span></span> <span data-ttu-id="8743b-241">Database Mail 設定檔是 Database Mail 帳戶的集合。</span><span class="sxs-lookup"><span data-stu-id="8743b-241">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="8743b-242">設定檔會在電子郵件伺服器無法連接時，提供替代的 Database Mail 帳戶，加強可靠性。</span><span class="sxs-lookup"><span data-stu-id="8743b-242">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="8743b-243">至少需要一個 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-243">At least one Database Mail account is required.</span></span> <span data-ttu-id="8743b-244">如需在設定檔中設定 Database Mail 帳戶之優先權的詳細資訊，請參閱 [建立 Database Mail 設定檔](create-a-database-mail-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="8743b-244">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="8743b-245">使用 [上移]\*\*\*\* 和 [下移]\*\*\*\* 按鈕，即可變更使用 Database Mail 帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-245">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="8743b-246">此順序是由一個值 (稱為序號) 決定。</span><span class="sxs-lookup"><span data-stu-id="8743b-246">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="8743b-247">[上移]\*\*\*\* 會減少序號，而 [下移]\*\*\*\* 會增加序號。</span><span class="sxs-lookup"><span data-stu-id="8743b-247">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="8743b-248">序號決定了 Database Mail 使用設定檔中之帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-248">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="8743b-249">如果是新的電子郵件訊息，Database Mail 會從序號最低的帳戶開始。</span><span class="sxs-lookup"><span data-stu-id="8743b-249">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="8743b-250">如果這個帳戶失敗，Database Mail 會使用序號次高的帳戶，依此類推，直到 Database Mail 傳送訊息成功為止，或直到序號最高的帳戶失敗為止。</span><span class="sxs-lookup"><span data-stu-id="8743b-250">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="8743b-251">如果序號最高的帳戶失敗，Database Mail 會暫停嘗試傳送郵件一段時間，這段時間是在 Database Mail **AccountRetryDelay** 參數中設定，然後從最低序號開始，再次開始嘗試傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-251">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="8743b-252">使用 Database Mail **AccountRetryAttempts** 參數，即可設定外部郵件處理序使用指定之設定檔內的每個帳戶，嘗試傳送電子郵件訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="8743b-252">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="8743b-253">您可以在 Database Mail 組態精靈的 [設定系統參數]\*\*\*\* 頁面上，設定 **AccountRetryDelay** 和 **AccountRetryAttempts** 參數。</span><span class="sxs-lookup"><span data-stu-id="8743b-253">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="8743b-254">[設定檔名稱]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8743b-254">**Profile name**</span></span>  
 <span data-ttu-id="8743b-255">輸入新設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-255">Type the name for the new profile.</span></span> <span data-ttu-id="8743b-256">系統會使用此名稱來建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-256">The profile is created with this name.</span></span> <span data-ttu-id="8743b-257">請勿使用現有設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-257">Do not use the name of an existing profile.</span></span>  
  
 <span data-ttu-id="8743b-258">**說明**</span><span class="sxs-lookup"><span data-stu-id="8743b-258">**Description**</span></span>  
 <span data-ttu-id="8743b-259">鍵入設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="8743b-259">Type a description for the profile.</span></span> <span data-ttu-id="8743b-260">描述是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-260">The description is optional.</span></span>  
  
 <span data-ttu-id="8743b-261">**SMTP 帳戶**</span><span class="sxs-lookup"><span data-stu-id="8743b-261">**SMTP accounts**</span></span>  
 <span data-ttu-id="8743b-262">為設定檔選擇一或多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-262">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="8743b-263">優先權會設定 Database Mail 使用這些帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-263">The priority sets the order in which Database Mail uses the accounts.</span></span> <span data-ttu-id="8743b-264">如果沒有列出任何帳戶，您必須按一下 [加入]\*\*\*\* 才能繼續，然後加入新的 SMTP 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-264">If no accounts are listed, you must click **Add** to continue, and add a new SMTP account.</span></span>  
  
 <span data-ttu-id="8743b-265">**加入**</span><span class="sxs-lookup"><span data-stu-id="8743b-265">**Add**</span></span>  
 <span data-ttu-id="8743b-266">將帳戶加入至設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-266">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="8743b-267">**移除**</span><span class="sxs-lookup"><span data-stu-id="8743b-267">**Remove**</span></span>  
 <span data-ttu-id="8743b-268">從設定檔移除選取的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-268">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="8743b-269">**上移**</span><span class="sxs-lookup"><span data-stu-id="8743b-269">**Move Up**</span></span>  
 <span data-ttu-id="8743b-270">增加選取之帳戶的優先權。</span><span class="sxs-lookup"><span data-stu-id="8743b-270">Increase the priority of the selected account.</span></span>  
  
 <span data-ttu-id="8743b-271">**下移**</span><span class="sxs-lookup"><span data-stu-id="8743b-271">**Move Down**</span></span>  
 <span data-ttu-id="8743b-272">減少選取之帳戶的優先權。</span><span class="sxs-lookup"><span data-stu-id="8743b-272">Decrease the priority of the selected account.</span></span>  
  

  
###  <a name="manage-existing-profile-page"></a><a name="ExistingProfile"></a><span data-ttu-id="8743b-273">管理現有的設定檔頁面面</span><span class="sxs-lookup"><span data-stu-id="8743b-273">Manage Existing Profile Page</span></span>  
 <span data-ttu-id="8743b-274">使用此頁面可管理現有的 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-274">Use this page to manage an existing Database Mail profile.</span></span> <span data-ttu-id="8743b-275">Database Mail 設定檔是 Database Mail 帳戶的集合。</span><span class="sxs-lookup"><span data-stu-id="8743b-275">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="8743b-276">設定檔會在電子郵件伺服器無法連接時，提供替代的 Database Mail 帳戶，加強可靠性。</span><span class="sxs-lookup"><span data-stu-id="8743b-276">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="8743b-277">至少需要一個 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-277">At least one Database Mail account is required.</span></span> <span data-ttu-id="8743b-278">如需在設定檔中設定 Database Mail 帳戶之優先權的詳細資訊，請參閱 [建立 Database Mail 設定檔](create-a-database-mail-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="8743b-278">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="8743b-279">使用 [上移]\*\*\*\* 和 [下移]\*\*\*\* 按鈕，即可變更使用 Database Mail 帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-279">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="8743b-280">此順序是由一個值 (稱為序號) 決定。</span><span class="sxs-lookup"><span data-stu-id="8743b-280">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="8743b-281">[上移]\*\*\*\* 會減少序號，而 [下移]\*\*\*\* 會增加序號。</span><span class="sxs-lookup"><span data-stu-id="8743b-281">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="8743b-282">序號決定了 Database Mail 使用設定檔中之帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-282">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="8743b-283">如果是新的電子郵件訊息，Database Mail 會從序號最低的帳戶開始。</span><span class="sxs-lookup"><span data-stu-id="8743b-283">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="8743b-284">如果這個帳戶失敗，Database Mail 會使用序號次高的帳戶，依此類推，直到 Database Mail 傳送訊息成功為止，或直到序號最高的帳戶失敗為止。</span><span class="sxs-lookup"><span data-stu-id="8743b-284">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="8743b-285">如果序號最高的帳戶失敗，Database Mail 會暫停嘗試傳送郵件一段時間，這段時間是在 Database Mail **AccountRetryDelay** 參數中設定，然後從最低序號開始，再次開始嘗試傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-285">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="8743b-286">使用 Database Mail **AccountRetryAttempts** 參數，即可設定外部郵件處理序使用指定之設定檔內的每個帳戶，嘗試傳送電子郵件訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="8743b-286">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="8743b-287">您可以在 Database Mail 組態精靈的 [設定系統參數]\*\*\*\* 頁面上，設定 **AccountRetryDelay** 和 **AccountRetryAttempts** 參數。</span><span class="sxs-lookup"><span data-stu-id="8743b-287">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="8743b-288">[設定檔名稱]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8743b-288">**Profile name**</span></span>  
 <span data-ttu-id="8743b-289">選取要管理之設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-289">Select the name of the profile to manage.</span></span>  
  
 <span data-ttu-id="8743b-290">**刪除**</span><span class="sxs-lookup"><span data-stu-id="8743b-290">**Delete**</span></span>  
 <span data-ttu-id="8743b-291">刪除選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-291">Delete the selected profile.</span></span> <span data-ttu-id="8743b-292">系統會提示您選取 [是]\*\*\*\* 來刪除選取的設定檔，並將任何未送出的郵件設為失敗，或選取 [否]\*\*\*\*，只有在沒有未送出的郵件時才刪除選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-292">You will be prompted to select **Yes** to delete the selected profile and to fail any unsent messages, or to select **No** to delete the selected profile only if there are no unsent messages.</span></span>  
  
 <span data-ttu-id="8743b-293">**說明**</span><span class="sxs-lookup"><span data-stu-id="8743b-293">**Description**</span></span>  
 <span data-ttu-id="8743b-294">檢視或變更選取之設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="8743b-294">View or change the description of the selected profile.</span></span> <span data-ttu-id="8743b-295">描述是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8743b-295">The description is optional.</span></span>  
  
 <span data-ttu-id="8743b-296">**SMTP 帳戶**</span><span class="sxs-lookup"><span data-stu-id="8743b-296">**SMTP accounts**</span></span>  
 <span data-ttu-id="8743b-297">為設定檔選擇一或多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-297">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="8743b-298">容錯移轉優先權會設定在發生容錯移轉時，Database Mail 使用帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="8743b-298">The failover priority sets the order in which Database Mail uses the account in case of a failover.</span></span>  
  
 <span data-ttu-id="8743b-299">**加入**</span><span class="sxs-lookup"><span data-stu-id="8743b-299">**Add**</span></span>  
 <span data-ttu-id="8743b-300">將帳戶加入至設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-300">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="8743b-301">**移除**</span><span class="sxs-lookup"><span data-stu-id="8743b-301">**Remove**</span></span>  
 <span data-ttu-id="8743b-302">從設定檔移除選取的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-302">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="8743b-303">**上移**</span><span class="sxs-lookup"><span data-stu-id="8743b-303">**Move Up**</span></span>  
 <span data-ttu-id="8743b-304">增加選取之帳戶的容錯移轉優先權。</span><span class="sxs-lookup"><span data-stu-id="8743b-304">Increase the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="8743b-305">**下移**</span><span class="sxs-lookup"><span data-stu-id="8743b-305">**Move Down**</span></span>  
 <span data-ttu-id="8743b-306">減少選取之帳戶的容錯移轉優先權。</span><span class="sxs-lookup"><span data-stu-id="8743b-306">Decrease the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="8743b-307">**優先順序**</span><span class="sxs-lookup"><span data-stu-id="8743b-307">**Priority**</span></span>  
 <span data-ttu-id="8743b-308">檢視帳戶的目前容錯移轉優先權。</span><span class="sxs-lookup"><span data-stu-id="8743b-308">View the current failover priority of the account.</span></span>  
  
 <span data-ttu-id="8743b-309">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-309">**Account name**</span></span>  
 <span data-ttu-id="8743b-310">檢視帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-310">View the name of the account.</span></span>  
  
 <span data-ttu-id="8743b-311">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="8743b-311">**E-mail Address**</span></span>  
 <span data-ttu-id="8743b-312">檢視帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-312">View the e-mail address of the account.</span></span>  
  

  
###  <a name="add-account-to-profile-page"></a><a name="AddAccount"></a><span data-ttu-id="8743b-313">將帳戶加入至設定檔頁面面</span><span class="sxs-lookup"><span data-stu-id="8743b-313">Add Account to Profile Page</span></span>  
 <span data-ttu-id="8743b-314">使用此頁面可選擇要加入至設定檔的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-314">Use this page to choose the account to add to the profile.</span></span> <span data-ttu-id="8743b-315">從 [帳戶名稱]\*\*\*\* 方塊中選擇現有的帳戶，或是按一下 [新增帳戶]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8743b-315">Either choose an existing account from the **Account name** box, or click **New Account**.</span></span>  
  
 <span data-ttu-id="8743b-316">**帳戶名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-316">**Account name**</span></span>  
 <span data-ttu-id="8743b-317">選取要加入至設定檔之帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-317">Select the name of the account to add to the profile.</span></span>  
  
 <span data-ttu-id="8743b-318">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="8743b-318">**E-mail address**</span></span>  
 <span data-ttu-id="8743b-319">檢視選取之帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-319">View the e-mail address for the selected account.</span></span> <span data-ttu-id="8743b-320">您無法從此頁面中變更電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-320">You cannot change the e-mail address from this page.</span></span> <span data-ttu-id="8743b-321">若要變更帳戶的電子郵件地址，請回到精靈的主要頁面，然後選取 [管理 Database Mail 帳戶和設定檔]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8743b-321">To change the e-mail address for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="8743b-322">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-322">**Server name**</span></span>  
 <span data-ttu-id="8743b-323">檢視選取之帳戶的郵件伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-323">View the mail server name for the selected account.</span></span> <span data-ttu-id="8743b-324">您無法從此頁面中變更伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-324">You cannot change the server name from this page.</span></span> <span data-ttu-id="8743b-325">若要變更帳戶的伺服器名稱，請回到精靈的主要頁面，然後選取 [管理 Database Mail 帳戶和設定檔]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8743b-325">To change the server name for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="8743b-326">**新增帳戶**</span><span class="sxs-lookup"><span data-stu-id="8743b-326">**New Account**</span></span>  
 <span data-ttu-id="8743b-327">建立新帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-327">Create a new account.</span></span>  
  

  
###  <a name="manage-accounts-and-profiles-page"></a><a name="AccountsProfiles"></a> <span data-ttu-id="8743b-328">管理帳戶和設定檔頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-328">Manage Accounts and Profiles Page</span></span>  
 <span data-ttu-id="8743b-329">使用此頁面可選擇用來管理設定檔或帳戶的工作。</span><span class="sxs-lookup"><span data-stu-id="8743b-329">Use this page to choose a task for managing a profile or account.</span></span>  
  
 <span data-ttu-id="8743b-330">**建立新帳戶**</span><span class="sxs-lookup"><span data-stu-id="8743b-330">**Create a new account**</span></span>  
 <span data-ttu-id="8743b-331">建立新帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-331">Create a new account.</span></span>  
  
 <span data-ttu-id="8743b-332">**檢視、變更或刪除現有的帳戶**</span><span class="sxs-lookup"><span data-stu-id="8743b-332">**View, change or delete an existing account**</span></span>  
 <span data-ttu-id="8743b-333">管理或刪除現有的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-333">Manage or delete an existing account.</span></span>  
  
 <span data-ttu-id="8743b-334">**建立新的設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-334">**Create a new profile**</span></span>  
 <span data-ttu-id="8743b-335">建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-335">Create a new profile.</span></span>  
  
 <span data-ttu-id="8743b-336">**查看、變更或刪除現有的設定檔。您也可以管理與設定檔相關聯的帳戶。**</span><span class="sxs-lookup"><span data-stu-id="8743b-336">**View, change or delete an existing profile. You can also manage accounts associated with the profile.**</span></span>  
 <span data-ttu-id="8743b-337">更新或刪除現有的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-337">Update or delete an existing profile.</span></span> <span data-ttu-id="8743b-338">此選項也可讓您管理與設定檔相關聯的帳戶。</span><span class="sxs-lookup"><span data-stu-id="8743b-338">This option also allows you to manage accounts associated with the profile.</span></span>  
  

  
###  <a name="manage-profile-security-public-tab"></a><a name="ProfileSecurityPublic"></a><span data-ttu-id="8743b-339">管理設定檔安全性，公用索引標籤</span><span class="sxs-lookup"><span data-stu-id="8743b-339">Manage Profile Security, Public Tab</span></span>  
 <span data-ttu-id="8743b-340">使用此頁面來設定公用設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-340">Use this page to configure a public profile.</span></span>  
  
 <span data-ttu-id="8743b-341">設定檔是公用或私人的。</span><span class="sxs-lookup"><span data-stu-id="8743b-341">Profiles are either public or private.</span></span> <span data-ttu-id="8743b-342">私人設定檔只有特定使用者或角色能夠存取。</span><span class="sxs-lookup"><span data-stu-id="8743b-342">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="8743b-343">公用設定檔允許擁有郵件主機資料庫 (**msdb**) 存取權的任何使用者或角色，使用該設定檔傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-343">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="8743b-344">設定檔可能是預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-344">A profile may be a default profile.</span></span> <span data-ttu-id="8743b-345">在此情況下，使用者或角色不必明確指定設定檔，就能使用設定檔傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-345">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="8743b-346">如果傳送電子郵件訊息的使用者或角色有預設的私人設定檔，Database Mail 就會使用該設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-346">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="8743b-347">如果使用者或角色沒有預設的私人設定檔， **sp_send_dbmail** 會使用 **msdb** 資料庫的預設公用設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-347">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="8743b-348">如果沒有使用者或角色的預設私人設定檔，而且沒有資料庫的預設公用設定檔， **sp_send_dbmail** 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="8743b-348">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span> <span data-ttu-id="8743b-349">只有一個設定檔可以標示為預設的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-349">Only one profile can be marked as the default profile.</span></span>  
  
 <span data-ttu-id="8743b-350">**公開**</span><span class="sxs-lookup"><span data-stu-id="8743b-350">**Public**</span></span>  
 <span data-ttu-id="8743b-351">選取此選項使指定的設定檔成為公用的。</span><span class="sxs-lookup"><span data-stu-id="8743b-351">Select this option to make the specified profile public.</span></span>  
  
 <span data-ttu-id="8743b-352">**設定檔名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-352">**Profile Name**</span></span>  
 <span data-ttu-id="8743b-353">顯示設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-353">Displays the name of the profile.</span></span>  
  
 <span data-ttu-id="8743b-354">**預設設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-354">**Default Profile**</span></span>  
 <span data-ttu-id="8743b-355">選取此選項使指定的設定檔成為預設的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-355">Select this option to make the specified profile the default profile.</span></span>  
  
 <span data-ttu-id="8743b-356">**只顯示現有的公用設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-356">**Show only existing public profiles**</span></span>  
 <span data-ttu-id="8743b-357">選取此選項，以便只顯示指定之資料庫中公用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-357">Select this option to show only public profiles in the specified database.</span></span>  
  

  
###  <a name="manage-profile-security-private-tab"></a><a name="ProfileSecurityPrivate"></a><span data-ttu-id="8743b-358">管理設定檔安全性，私用索引標籤</span><span class="sxs-lookup"><span data-stu-id="8743b-358">Manage Profile Security, Private Tab</span></span>  
 <span data-ttu-id="8743b-359">使用此頁面來設定私人設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-359">Use this page to configure a private profile.</span></span>  
  
 <span data-ttu-id="8743b-360">設定檔是公用或私人的。</span><span class="sxs-lookup"><span data-stu-id="8743b-360">Profiles are either public or private.</span></span> <span data-ttu-id="8743b-361">私人設定檔只有特定使用者或角色能夠存取。</span><span class="sxs-lookup"><span data-stu-id="8743b-361">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="8743b-362">公用設定檔允許擁有郵件主機資料庫 (**msdb**) 存取權的任何使用者或角色，使用該設定檔傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-362">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="8743b-363">設定檔可能是預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-363">A profile may be a default profile.</span></span> <span data-ttu-id="8743b-364">在此情況下，使用者或角色不必明確指定設定檔，就能使用設定檔傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-364">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="8743b-365">如果傳送電子郵件訊息的使用者或角色有預設的私人設定檔，Database Mail 就會使用該設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-365">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="8743b-366">如果使用者或角色沒有預設的私人設定檔， **sp_send_dbmail** 會使用 **msdb** 資料庫的預設公用設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-366">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="8743b-367">如果沒有使用者或角色的預設私人設定檔，而且沒有資料庫的預設公用設定檔， **sp_send_dbmail** 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="8743b-367">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span>  
  
 <span data-ttu-id="8743b-368">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="8743b-368">**User name**</span></span>  
 <span data-ttu-id="8743b-369">選取 **msdb** 資料庫中使用者或角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-369">Select the name of a user or role in the **msdb** database.</span></span>  
  
 <span data-ttu-id="8743b-370">**存取**</span><span class="sxs-lookup"><span data-stu-id="8743b-370">**Access**</span></span>  
 <span data-ttu-id="8743b-371">選取使用者或角色是否能夠存取指定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-371">Select whether the user or role has access to the specified profile.</span></span>  
  
 <span data-ttu-id="8743b-372">[設定檔名稱]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8743b-372">**Profile name**</span></span>  
 <span data-ttu-id="8743b-373">檢視設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8743b-373">View the name of the profile.</span></span>  
  
 <span data-ttu-id="8743b-374">**是預設的設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-374">**Is Default Profile**</span></span>  
 <span data-ttu-id="8743b-375">選取設定檔是否是使用者或角色的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-375">Select whether the profile is the default profile for the user or role.</span></span> <span data-ttu-id="8743b-376">每個使用者或角色只可以有一個預設的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-376">Each user or role may have only one default profile.</span></span>  
  
 <span data-ttu-id="8743b-377">**只顯示此使用者的現有私人設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-377">**Show only existing private profiles for this user**</span></span>  
 <span data-ttu-id="8743b-378">選取此選項，只顯示指定之使用者或角色已經擁有存取權的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-378">Select this option to display only profiles that the specified user or role already has access to.</span></span>  
  

  
###  <a name="configure-system-parameters"></a><a name="SystemParameters"></a><span data-ttu-id="8743b-379">設定系統參數</span><span class="sxs-lookup"><span data-stu-id="8743b-379">Configure System Parameters</span></span>  
 <span data-ttu-id="8743b-380">使用此頁面來指定 Database Mail 系統參數。</span><span class="sxs-lookup"><span data-stu-id="8743b-380">Use this page to specify Database Mail system parameters.</span></span> <span data-ttu-id="8743b-381">檢視系統參數以及每個參數目前的值。</span><span class="sxs-lookup"><span data-stu-id="8743b-381">View the system parameters and the current value of each parameter.</span></span> <span data-ttu-id="8743b-382">選取參數，以便在資訊窗格中檢視簡短的描述。</span><span class="sxs-lookup"><span data-stu-id="8743b-382">Select a parameter to view a short description in the information pane.</span></span>  
  
 <span data-ttu-id="8743b-383">**帳戶重試嘗試**</span><span class="sxs-lookup"><span data-stu-id="8743b-383">**Account Retry Attempts**</span></span>  
 <span data-ttu-id="8743b-384">外部郵件處理序嘗試利用指定設定檔中的每個帳戶來傳送電子郵件訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="8743b-384">The number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="8743b-385">**帳戶重試延遲 (秒)**</span><span class="sxs-lookup"><span data-stu-id="8743b-385">**Account Retry Delay (seconds)**</span></span>  
 <span data-ttu-id="8743b-386">外部郵件處理序在使用設定檔中的所有帳戶，來嘗試傳遞訊息之後，其在再次嘗試使用所有帳戶之前，所需等候的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="8743b-386">The amount of time, in seconds, for the external mail process to wait after it tries to deliver a message using all accounts in the profile before it attempts all accounts again.</span></span>  
  
 <span data-ttu-id="8743b-387">**檔案大小上限 (位元組)**</span><span class="sxs-lookup"><span data-stu-id="8743b-387">**Maximum File Size (Bytes)**</span></span>  
 <span data-ttu-id="8743b-388">附件的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="8743b-388">The maximum size of an attachment, in bytes.</span></span>  
  
 <span data-ttu-id="8743b-389">**禁止的附加檔案副檔名**</span><span class="sxs-lookup"><span data-stu-id="8743b-389">**Prohibited Attachment File Extensions**</span></span>  
 <span data-ttu-id="8743b-390">無法作為電子郵件訊息附件來傳送的副檔名清單 (以逗號分隔)。</span><span class="sxs-lookup"><span data-stu-id="8743b-390">A comma-separated list of extensions which cannot be sent as an attachment to an e-mail message.</span></span> <span data-ttu-id="8743b-391">按一下瀏覽按鈕 ([...]\*\*\*\*)，加入其他副檔名。</span><span class="sxs-lookup"><span data-stu-id="8743b-391">Click the browse button (**...**) to add additional extensions.</span></span>  
  
 <span data-ttu-id="8743b-392">**Database Mail 可執行檔最小存留期間 (秒)**</span><span class="sxs-lookup"><span data-stu-id="8743b-392">**Database Mail Executable Minimum Lifetime (seconds)**</span></span>  
 <span data-ttu-id="8743b-393">外部郵件處理序維持使用中的最短時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="8743b-393">The minimum amount of time, in seconds, that the external mail process remains active.</span></span> <span data-ttu-id="8743b-394">只要在 Database Mail 佇列中有電子郵件，此處理序就會保持在使用中。</span><span class="sxs-lookup"><span data-stu-id="8743b-394">The process remains active as long as there are e-mails in the Database Mail queue.</span></span> <span data-ttu-id="8743b-395">此參數指定當沒有要處理的訊息時，處理序保持在使用中的時間。</span><span class="sxs-lookup"><span data-stu-id="8743b-395">This parameter specifies the time the process remains active if there are no messages to process.</span></span>  
  
 <span data-ttu-id="8743b-396">**記錄層級**</span><span class="sxs-lookup"><span data-stu-id="8743b-396">**Logging level**</span></span>  
 <span data-ttu-id="8743b-397">指定哪些訊息要記錄在 Database Mail 記錄中。</span><span class="sxs-lookup"><span data-stu-id="8743b-397">Specify which messages are recorded in the Database Mail log.</span></span> <span data-ttu-id="8743b-398">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="8743b-398">Possible values are:</span></span>  
  
-   <span data-ttu-id="8743b-399">一般 - 只記錄錯誤</span><span class="sxs-lookup"><span data-stu-id="8743b-399">Normal - logs only errors</span></span>  
  
-   <span data-ttu-id="8743b-400">擴充 - 記錄錯誤、警告以及資訊性訊息</span><span class="sxs-lookup"><span data-stu-id="8743b-400">Extended - logs errors, warnings, and informational messages</span></span>  
  
-   <span data-ttu-id="8743b-401">詳細資訊 - 記錄錯誤、警告、資訊性訊息、成功訊息以及其他內部訊息。</span><span class="sxs-lookup"><span data-stu-id="8743b-401">Verbose - logs errors, warnings, informational messages, success messages, and additional internal messages.</span></span> <span data-ttu-id="8743b-402">使用詳細資訊記錄來進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8743b-402">Use verbose logging for troubleshooting.</span></span>  
  
 <span data-ttu-id="8743b-403">預設值是擴充。</span><span class="sxs-lookup"><span data-stu-id="8743b-403">Default value is Extended.</span></span>  
  
 <span data-ttu-id="8743b-404">**全部重設**</span><span class="sxs-lookup"><span data-stu-id="8743b-404">**Reset All**</span></span>  
 <span data-ttu-id="8743b-405">選取此選項，將頁面上的值都重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="8743b-405">Select this option to reset the values on the page to the default values.</span></span>  
  

  
###  <a name="complete-the-wizard-page"></a><a name="CompleteWizard"></a><span data-ttu-id="8743b-406">完成嚮導頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-406">Complete the Wizard Page</span></span>  
 <span data-ttu-id="8743b-407">使用此頁面來檢閱 [Database Mail 組態精靈]\*\*\*\* 將要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8743b-407">Use this page to review the actions that **Database Mail Configuration Wizard** will perform.</span></span> <span data-ttu-id="8743b-408">在精靈結束之前將不會做任何變更。</span><span class="sxs-lookup"><span data-stu-id="8743b-408">No changes are made until you finish the wizard.</span></span>  
  

  
###  <a name="send-test-e-mail-page"></a><a name="TestEmail"></a><span data-ttu-id="8743b-409">傳送測試電子郵件頁面</span><span class="sxs-lookup"><span data-stu-id="8743b-409">Send Test E-Mail Page</span></span>  
 <span data-ttu-id="8743b-410">使用 [從 <執行個體名稱>__ 傳送測試電子郵件]\*\*\*\* 頁面，以使用指定的 Database Mail 設定檔傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="8743b-410">Use the **Send Test E-Mail from**_<instance_name>_ page to send an e-mail message using the specified Database Mail profile.</span></span> <span data-ttu-id="8743b-411">只有 **系統管理員** 固定伺服器角色的成員，才可以使用此頁面來傳送測試電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8743b-411">Only members of the **sysadmin** fixed server role can send test e-mail using this page.</span></span>  
  
 <span data-ttu-id="8743b-412">**Database Mail 設定檔**</span><span class="sxs-lookup"><span data-stu-id="8743b-412">**Database Mail Profile**</span></span>  
 <span data-ttu-id="8743b-413">從清單中選取 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-413">Select a Database Mail profile from the list.</span></span> <span data-ttu-id="8743b-414">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="8743b-414">This is a required field.</span></span> <span data-ttu-id="8743b-415">如果未顯示任何設定檔，就表示沒有設定檔，或者您沒有設定檔的存取權限。</span><span class="sxs-lookup"><span data-stu-id="8743b-415">If no profiles are shown, there are no profiles or you do not have permission to a profile.</span></span> <span data-ttu-id="8743b-416">使用 **[Database Mail 組態精靈]** 來建立及設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-416">Use the **Database Mail Configuration Wizard** to create and configure profiles.</span></span> <span data-ttu-id="8743b-417">如果未列出任何設定檔，請使用 Database Mail 組態精靈來建立供您使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-417">If no profiles are listed, use the Database Mail Configuration Wizard to create a profile for your use.</span></span>  
  
 <span data-ttu-id="8743b-418">**若要**</span><span class="sxs-lookup"><span data-stu-id="8743b-418">**To**</span></span>  
 <span data-ttu-id="8743b-419">訊息收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8743b-419">The e-mail address of the message recipients.</span></span> <span data-ttu-id="8743b-420">至少需要一位收件者。</span><span class="sxs-lookup"><span data-stu-id="8743b-420">At least one recipient is required.</span></span>  
  
 <span data-ttu-id="8743b-421">**主旨**</span><span class="sxs-lookup"><span data-stu-id="8743b-421">**Subject**</span></span>  
 <span data-ttu-id="8743b-422">測試電子郵件的主旨列。</span><span class="sxs-lookup"><span data-stu-id="8743b-422">The subject line for the test e-mail.</span></span> <span data-ttu-id="8743b-423">變更預設主旨，以便更適當地識別您的電子郵件進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8743b-423">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="8743b-424">**本文**</span><span class="sxs-lookup"><span data-stu-id="8743b-424">**Body**</span></span>  
 <span data-ttu-id="8743b-425">測試電子郵件的本文。</span><span class="sxs-lookup"><span data-stu-id="8743b-425">The body of the test e-mail.</span></span> <span data-ttu-id="8743b-426">變更預設主旨，以便更適當地識別您的電子郵件進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8743b-426">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="8743b-427">[Database Mail 測試電子郵件]\*\*\*\* 對話方塊會確認 Database Mail 已嘗試傳送測試訊息，並提供測試電子郵件訊息的 **mailitem_id**。</span><span class="sxs-lookup"><span data-stu-id="8743b-427">The **Database Mail Test E-Mail** dialog box confirms that the test message that Database Mail attempted to send the message and provides the **mailitem_id** for the test e-mail message.</span></span> <span data-ttu-id="8743b-428">與收件者聯繫來判斷電子郵件是否送達。</span><span class="sxs-lookup"><span data-stu-id="8743b-428">Check with the recipient to determine if the e-mail arrived.</span></span> <span data-ttu-id="8743b-429">電子郵件一般都會在數分鐘內收到，但是電子郵件可能因為緩慢的網路效能、在郵件伺服器上積存訊息，或伺服器暫時不能使用等原因而延遲。</span><span class="sxs-lookup"><span data-stu-id="8743b-429">Normally e-mail is received in a few minutes, but the e-mail can be delayed because of slow network performance, a backlog of messages at the mail server, or if the server is temporarily unavailable.</span></span> <span data-ttu-id="8743b-430">使用 **mailitem_id** 來進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8743b-430">Use the **mailitem_id** for troubleshooting.</span></span>  
  
 <span data-ttu-id="8743b-431">**傳送電子郵件**</span><span class="sxs-lookup"><span data-stu-id="8743b-431">**Sent e-mail**</span></span>  
 <span data-ttu-id="8743b-432">測試電子郵件訊息的 **mailitem_id** 。</span><span class="sxs-lookup"><span data-stu-id="8743b-432">The **mailitem_id** of the test e-mail message.</span></span>  
  
 <span data-ttu-id="8743b-433">**疑難排解**</span><span class="sxs-lookup"><span data-stu-id="8743b-433">**Troubleshoot**</span></span>  
 <span data-ttu-id="8743b-434">按一下以開啟《線上叢書》的 [Database Mail 疑難排解](https://msdn.microsoft.com/library/ms188663.aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="8743b-434">Click to open Books Online to the [Troubleshooting Database Mail](https://msdn.microsoft.com/library/ms188663.aspx)topic.</span></span>  
  

  
##  <a name="using-templates"></a><a name="Template"></a> <span data-ttu-id="8743b-435">使用範本</span><span class="sxs-lookup"><span data-stu-id="8743b-435">Using Templates</span></span>  
 <span data-ttu-id="8743b-436">**若要建立 Database Mail 組態指令碼**</span><span class="sxs-lookup"><span data-stu-id="8743b-436">**To create a Database Mail configuration script**</span></span>  
  
1.  <span data-ttu-id="8743b-437">在 [檢視]\*\*\*\* 功能表中，選取 [範本總管]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8743b-437">On the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="8743b-438">在 [範本總管]\*\*\*\* 視窗中，展開 [Database Mail]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8743b-438">In the **Template Explorer** window, expand the **Database Mail** folder.</span></span>  
  
3.  <span data-ttu-id="8743b-439">按兩下 [Simple Database Mail 組態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8743b-439">Double-click **Simple Database Mail Configuration**.</span></span> <span data-ttu-id="8743b-440">就會在新查詢視窗中開啟範本。</span><span class="sxs-lookup"><span data-stu-id="8743b-440">The template opens in a new query window.</span></span>  
  
4.  <span data-ttu-id="8743b-441">在 [查詢]\*\*\*\* 功能表上，選取 [指定範本參數的值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8743b-441">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="8743b-442">即會開啟 [取代範本參數]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="8743b-442">The **Replace Template Parameters** window opens.</span></span>  
  
5.  <span data-ttu-id="8743b-443">輸入 **profile_name**、 **account_name**、 **SMTP_servername**、 **email_address**和 **display_name**的值。</span><span class="sxs-lookup"><span data-stu-id="8743b-443">Type values for the **profile_name**, **account_name**, **SMTP_servername**, **email_address**, and **display_name**.</span></span> <span data-ttu-id="8743b-444">SQL Server Management Studio 就會將您提供的值填入範本中。</span><span class="sxs-lookup"><span data-stu-id="8743b-444">SQL Server Management Studio fills in the template with the values you provide.</span></span>  
  
6.  <span data-ttu-id="8743b-445">執行指令碼以建立組態。</span><span class="sxs-lookup"><span data-stu-id="8743b-445">Execute the script to create the configuration.</span></span>  
  
7.  <span data-ttu-id="8743b-446">此指令碼不會將資料庫使用者存取權授與給設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-446">The script does not grant any database users access to the profile.</span></span> <span data-ttu-id="8743b-447">因此，依預設只有 **系統管理員** 固定安全性角色的成員才能使用此設定檔。</span><span class="sxs-lookup"><span data-stu-id="8743b-447">Therefore, by default, the profile can only be used by members of the **sysadmin** fixed security role.</span></span> <span data-ttu-id="8743b-448">如需授與設定檔存取權限的詳細資訊，請參閱 [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8743b-448">For more information about granting access to profiles, see [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)</span></span>  
  
  
