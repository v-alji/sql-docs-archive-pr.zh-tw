---
title: Database Mail 組態物件 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlimail.manageexistingaccount.f1
- sql12.swb.sqlimail.addaccounttoprofile.f1
- sql12.swb.sqlmailconfiguration.f1
- sql12.swb.sqlimail.profileandaccountmanagement.f1
- sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- sql12.swb.sqlimail.newsqlimailaccount.f1
- sql12.swb.sqlimail.configuresystem.f1
- sql12.swb.sqlimail.selectconfiguration.f1
- sql12.swb.sqlimail.newprofile.f1
- sql12.swb.sqlimail.manageexistingprofile.f1
- sql12.swb.sqlimail.welcome.f1
- sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- sql12.swb.sqlimail.completewizard.f1
- sql12.swb.sqlimail.newaccount.f1
helpviewer_keywords:
- Database Mail [SQL Server], configuration objects
- Database Mail [SQL Server], accounts
- configuration objects [Database Mail]
- Database Mail [SQL Server], profiles
- profiles [SQL Server], Database Mail
- accounts [Database Mail]
ms.assetid: 03f6e4c0-04ff-490a-bd91-637806215bd1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45dd4bfc8cdb382f9ad093e92c5939986a9db8e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709626"
---
# <a name="database-mail-configuration-objects"></a><span data-ttu-id="5c259-102">Database Mail 組態物件</span><span class="sxs-lookup"><span data-stu-id="5c259-102">Database Mail Configuration Objects</span></span>
  <span data-ttu-id="5c259-103">Database Mail 包含兩個設定物件：這些資料庫設定物件提供您方法，用來設定 Database Mail 從資料庫應用程式或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 傳送電子郵件時應使用的設定。</span><span class="sxs-lookup"><span data-stu-id="5c259-103">Database Mail has two configuration objects: The database configuration objects provide a way for you to configure the settings that Database mail should use when sending an email from your database application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="5c259-104">Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="5c259-104">Database Mail accounts</span></span>  
  
-   <span data-ttu-id="5c259-105">Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="5c259-105">Database Mail profiles</span></span>  
  
  
##  <a name="database-mail-configuration-object-relationship"></a><a name="VisualElement"></a> <span data-ttu-id="5c259-106">Database Mail 組態物件關聯性</span><span class="sxs-lookup"><span data-stu-id="5c259-106">Database Mail Configuration Object Relationship</span></span>  
 <span data-ttu-id="5c259-107">下圖說明顯示兩個設定檔、三個帳戶及三個使用者。</span><span class="sxs-lookup"><span data-stu-id="5c259-107">The illustration shows two profiles, three accounts, and three users.</span></span> <span data-ttu-id="5c259-108">「使用者 1」有「設定檔 1」的存取權，前者使用「帳戶 1」及「帳戶 2」。</span><span class="sxs-lookup"><span data-stu-id="5c259-108">User 1 has access to Profile 1, which uses Account 1 and Account 2.</span></span> <span data-ttu-id="5c259-109">「使用者 3」有「設定檔 2」的存取權，而「設定檔 2」使用「帳戶 3」及「帳戶 3」。</span><span class="sxs-lookup"><span data-stu-id="5c259-109">User 3 has access to Profile 2, which uses Account 2 and Account 3.</span></span> <span data-ttu-id="5c259-110">「使用者 2」有「設定檔 1」及「設定檔 2」的存取權。</span><span class="sxs-lookup"><span data-stu-id="5c259-110">User 2 has access to both Profile 1 and Profile 2.</span></span>  
  
 <span data-ttu-id="5c259-111">![使用者、設定檔與帳戶的關聯性](../../database-engine/media/databasemailprofileaccount.gif "使用者、設定檔與帳戶的關聯性")</span><span class="sxs-lookup"><span data-stu-id="5c259-111">![Relationship of users, profiles, and accounts](../../database-engine/media/databasemailprofileaccount.gif "Relationship of users, profiles, and accounts")</span></span>  
  
  
##  <a name="database-mail-account"></a><a name="DBAccount"></a> <span data-ttu-id="5c259-112">Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="5c259-112">Database Mail Account</span></span>  
 <span data-ttu-id="5c259-113">Database Mail 帳戶包含 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用來將電子郵件訊息傳送到 SMTP 伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-113">A Database Mail account contains the information that Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="5c259-114">每個帳戶包含一個電子郵件伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-114">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="5c259-115">Database Mail 支援三種與 SMTP 伺服器溝通的驗證方法：</span><span class="sxs-lookup"><span data-stu-id="5c259-115">A Database Mail supports three methods of authentication to communicate with an SMTP server:</span></span>  
  
-   <span data-ttu-id="5c259-116">Windows 驗證：Database Mail 使用 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows 服務帳戶的憑證進行 SMTP 伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="5c259-116">Windows Authentication: Database Mail uses the credentials of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows service account for authentication on the SMTP server.</span></span>  
  
-   <span data-ttu-id="5c259-117">基本驗證：Database Mail 使用指定的使用者名稱與密碼來進行 SMTP 伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="5c259-117">Basic Authentication:  Database Mail uses the username and password specified to authenticate on the SMTP server.</span></span>  
  
-   <span data-ttu-id="5c259-118">匿名驗證：SMTP 伺服器不需要任何驗證。</span><span class="sxs-lookup"><span data-stu-id="5c259-118">Anonymous Authentication:  The SMTP server does not require any authentication.</span></span>  <span data-ttu-id="5c259-119">Database Mail 將不會使用任何認證來進行 SMTP 伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="5c259-119">Database Mail will not use any credentials to authenticate on the SMTP server.</span></span>  
  
 <span data-ttu-id="5c259-120">帳戶資訊儲存在 **msdb** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5c259-120">Account information is stored in the **msdb** database.</span></span> <span data-ttu-id="5c259-121">每個帳戶都是由下列資訊組成：</span><span class="sxs-lookup"><span data-stu-id="5c259-121">Each account consists of the following information:</span></span>  
  
-   <span data-ttu-id="5c259-122">帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c259-122">The name of the account.</span></span>  
  
-   <span data-ttu-id="5c259-123">帳戶的描述。</span><span class="sxs-lookup"><span data-stu-id="5c259-123">A description of the account.</span></span>  
  
-   <span data-ttu-id="5c259-124">帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5c259-124">The e-mail address of the account.</span></span>  
  
-   <span data-ttu-id="5c259-125">帳戶的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5c259-125">The display name for the account.</span></span>  
  
-   <span data-ttu-id="5c259-126">用來作為帳戶回覆資訊的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5c259-126">The e-mail address to use as the reply-to information for the account.</span></span>  
  
-   <span data-ttu-id="5c259-127">電子郵件伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c259-127">The name of the e-mail server.</span></span>  
  
-   <span data-ttu-id="5c259-128">電子郵件伺服器的類型。</span><span class="sxs-lookup"><span data-stu-id="5c259-128">The type of the e-mail server.</span></span> <span data-ttu-id="5c259-129">針對 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，此一律為簡易郵件傳輸通訊協定 (SMTP)。</span><span class="sxs-lookup"><span data-stu-id="5c259-129">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this is always Simple Mail Transfer Protocol(SMTP).</span></span>  
  
-   <span data-ttu-id="5c259-130">電子郵件伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="5c259-130">The port number of the e-mail server.</span></span>  
  
-   <span data-ttu-id="5c259-131">位元資料行會指出 SMTP 郵件伺服器的連接是否使用安全通訊端層 (SSL) 來建立。</span><span class="sxs-lookup"><span data-stu-id="5c259-131">A bit column indicating whether the connection to the SMTP mail server is made using Secure Sockets Layer (SSL).</span></span>  
  
-   <span data-ttu-id="5c259-132">位元資料行會指出 SMTP 伺服器的連接是否使用為 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]所設定的憑證來建立。</span><span class="sxs-lookup"><span data-stu-id="5c259-132">A bit column indicating whether the connection to the SMTP server is made using the credentials configured for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5c259-133">用來驗證電子郵件伺服器的使用者名稱 (若電子郵件伺服器需要驗證的話)。</span><span class="sxs-lookup"><span data-stu-id="5c259-133">The user name to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
-   <span data-ttu-id="5c259-134">用來驗證電子郵件伺服器的密碼 (若電子郵件伺服器需要驗證的話)。</span><span class="sxs-lookup"><span data-stu-id="5c259-134">The password to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
 <span data-ttu-id="5c259-135">「Database Mail 組態精靈」提供一個便捷的方式來建立及管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-135">The Database Mail Configuration Wizard provides a convenient way to create and manage accounts.</span></span> <span data-ttu-id="5c259-136">您也可以使用 **msdb** 中的組態預存程序來建立及管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-136">You can also use the configuration stored procedures in **msdb** to create and manage accounts.</span></span>  
  
  
##  <a name="database-mail-profile"></a><a name="DBProfile"></a> <span data-ttu-id="5c259-137">Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="5c259-137">Database Mail Profile</span></span>  
 <span data-ttu-id="5c259-138">Database Mail 設定檔是相關 Database Mail 帳戶的排序集合。</span><span class="sxs-lookup"><span data-stu-id="5c259-138">A Database Mail profile is an ordered collection of related Database Mail accounts.</span></span> <span data-ttu-id="5c259-139">使用 Database Mail 傳送電子郵件的應用程式會指定設定檔，而不是直接使用帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-139">Applications that send e-mail using Database Mail specify profiles, instead of using accounts directly.</span></span> <span data-ttu-id="5c259-140">將個別電子郵件伺服器的資訊與應用程式所使用的物件區隔開來，可以增進彈性及可靠性：設定檔會提供自動容錯移轉功能，所以如果有一部電子郵件伺服器沒有回應，Database Mail 就會自動將郵件傳送至另一部電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="5c259-140">Separating information about the individual e-mail servers from the objects that the application uses improves flexibility and reliability: profiles provide automatic failover, so that if one e-mail server is unresponsive, Database Mail can automatically send mail to another e-mail server.</span></span> <span data-ttu-id="5c259-141">資料庫管理員不需要變更應用程式的程式碼或作業步驟，即可加入、移除或重新設定帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-141">Database administrators can add, remove, or reconfigure accounts without requiring changes to application code or job steps.</span></span>  
  
 <span data-ttu-id="5c259-142">設定檔也可以協助資料庫管理員控制電子郵件的存取。</span><span class="sxs-lookup"><span data-stu-id="5c259-142">Profiles also help database administrators control access to e-mail.</span></span> <span data-ttu-id="5c259-143">必須要有 **DatabaseMailUserRole** 成員資格，才能傳送 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="5c259-143">Membership in the **DatabaseMailUserRole** is required to send Database Mail.</span></span> <span data-ttu-id="5c259-144">管理員可以利用設定檔所提供的額外彈性來控制傳送郵件的人員及使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-144">Profiles provide additional flexibility for administrators to control who sends mail and which accounts are used.</span></span>  
  
 <span data-ttu-id="5c259-145">設定檔可能是公用或私人的。</span><span class="sxs-lookup"><span data-stu-id="5c259-145">A profile may be public or private.</span></span>  
  
 <span data-ttu-id="5c259-146">**msdb** 資料庫中之 **DatabaseMailUserRole** 資料庫角色的所有成員都可以存取 **公用設定檔** 。</span><span class="sxs-lookup"><span data-stu-id="5c259-146">**Public profiles** are available for all members of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span> <span data-ttu-id="5c259-147">它們讓 **DatabaseMailUserRole** 角色的所有成員可以使用設定檔傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="5c259-147">They allow all members of the **DatabaseMailUserRole** role to send e-mail using the profile.</span></span>  
  
 <span data-ttu-id="5c259-148">**msdb** 資料庫中的安全性主體會定義 **私人設定檔** 。</span><span class="sxs-lookup"><span data-stu-id="5c259-148">**Private profiles** are defined for security principals in the **msdb** database.</span></span> <span data-ttu-id="5c259-149">它們只容許指定的資料庫使用者、角色和 **sysadmin** 固定伺服器角色的成員，使用該設定檔來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="5c259-149">They allow only specified database users, roles, and members of the **sysadmin** fixed server role to send e-mail using the profile.</span></span> <span data-ttu-id="5c259-150">設定檔依預設是私人的，而且只有 **sysadmin** 固定伺服器角色的成員才能存取。</span><span class="sxs-lookup"><span data-stu-id="5c259-150">By default, a profile is private, and allows access only to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="5c259-151">若要使用私人設定檔， **sysadmin** 必須授與使用者權限，才能夠使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="5c259-151">To use a private profile, **sysadmin** must grant users permission to use the profile.</span></span> <span data-ttu-id="5c259-152">此外， **sp_send_dbmail** 預存程序的 EXECUTE 權限只授與 **DatabaseMailUserRole**的成員。</span><span class="sxs-lookup"><span data-stu-id="5c259-152">Additionally, EXECUTE permission on the **sp_send_dbmail** stored procedure is only granted to members of the **DatabaseMailUserRole**.</span></span> <span data-ttu-id="5c259-153">系統管理員必須將使用者加入 **DatabaseMailUserRole** 資料庫角色，使用者才能夠傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="5c259-153">A system administrator must add the user to the **DatabaseMailUserRole** database role for the user to send e-mail messages.</span></span>  
  
 <span data-ttu-id="5c259-154">萬一電子郵件伺服器無法連上或無法處理訊息，設定檔將可改善其可靠性。</span><span class="sxs-lookup"><span data-stu-id="5c259-154">Profiles improve reliability in cases where an e-mail server becomes unreachable or unable to process messages.</span></span> <span data-ttu-id="5c259-155">設定檔中的每個帳戶都有序號。</span><span class="sxs-lookup"><span data-stu-id="5c259-155">Each account in the profile has a sequence number.</span></span> <span data-ttu-id="5c259-156">序號決定了 Database Mail 使用設定檔中之帳戶的順序。</span><span class="sxs-lookup"><span data-stu-id="5c259-156">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="5c259-157">對於新的電子郵件訊息，Database Mail 會使用最後一個成功傳送訊息的帳戶，或若是訊息尚未傳送，就使用最低序號的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-157">For a new e-mail message, Database Mail uses the last account that sent a message successfully, or the account that has the lowest sequence number if no message has yet been sent.</span></span> <span data-ttu-id="5c259-158">如果這個帳戶失敗，Database Mail 會使用序號次高的帳戶，依此類推，直到 Database Mail 傳送訊息成功為止，或直到序號最高的帳戶失敗為止。</span><span class="sxs-lookup"><span data-stu-id="5c259-158">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="5c259-159">如果序號最高的帳戶失敗，Database Mail 會在 **sysmail_configure_sp** 的 **AccountRetryDelay**參數所設定的時間之內，暫停傳送郵件，之後，再從最低的序號開始，重新嘗試傳送郵件的處理序。</span><span class="sxs-lookup"><span data-stu-id="5c259-159">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the **AccountRetryDelay** parameter of **sysmail_configure_sp**, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="5c259-160">請利用 **sysmail_configure_sp** 的 **AccountRetryAttempts**參數，設定外部郵件處理序嘗試利用指定設定檔中的每個帳戶，來傳送電子郵件訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="5c259-160">Use the **AccountRetryAttempts** parameter of **sysmail_configure_sp**, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="5c259-161">如果有多個序號相同的帳戶存在，Database Mail 只會將其中一個帳戶用在給定的電子郵件訊息上。</span><span class="sxs-lookup"><span data-stu-id="5c259-161">If more than one account exists with the same sequence number, Database Mail only uses one of those accounts for a given e-mail message.</span></span> <span data-ttu-id="5c259-162">在這個情況下，Database Mail 並無法保證這個序號會用到哪個帳戶，也無法保證各訊息會用到相同的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-162">In this case, Database Mail makes no guarantees as to which of the accounts is used for that sequence number or that the same account is used from message to message.</span></span>  
  
  
##  <a name="database-mail-configuration-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5c259-163">Database Mail 組態工作</span><span class="sxs-lookup"><span data-stu-id="5c259-163">Database Mail Configuration Tasks</span></span>  
 <span data-ttu-id="5c259-164">下表描述 Database Mail 組態工作。</span><span class="sxs-lookup"><span data-stu-id="5c259-164">The following table describes the Database Mail configuration tasks.</span></span>  
  
|<span data-ttu-id="5c259-165">組態工作</span><span class="sxs-lookup"><span data-stu-id="5c259-165">Configuration Task</span></span>|<span data-ttu-id="5c259-166">主題連結</span><span class="sxs-lookup"><span data-stu-id="5c259-166">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="5c259-167">描述如何建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="5c259-167">Describes how to create a Database Mail accounts</span></span>|[<span data-ttu-id="5c259-168">建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="5c259-168">Create a Database Mail Account</span></span>](create-a-database-mail-account.md)|  
|<span data-ttu-id="5c259-169">描述如何建立 Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="5c259-169">Describes how to Create Database Mail profiles</span></span>|[<span data-ttu-id="5c259-170">建立 Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="5c259-170">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)|  
|<span data-ttu-id="5c259-171">描述如何設定 Database Mail</span><span class="sxs-lookup"><span data-stu-id="5c259-171">Describes how to Configure Database mail</span></span>|[<span data-ttu-id="5c259-172">設定 Database Mail</span><span class="sxs-lookup"><span data-stu-id="5c259-172">Configure Database Mail</span></span>](configure-database-mail.md)|  
|<span data-ttu-id="5c259-173">描述如何使用範本建立 Database Mail 組態指令碼</span><span class="sxs-lookup"><span data-stu-id="5c259-173">Describes how to create a Database Mail configuration script using templates</span></span>||  
  
  
##  <a name="additional-database-configuration-tasks-system-stored-procedures"></a><a name="Add_Tasks"></a> <span data-ttu-id="5c259-174">其他資料庫組態工作 (系統預存程序)</span><span class="sxs-lookup"><span data-stu-id="5c259-174">Additional Database Configuration Tasks (System Stored Procedures)</span></span>  
 <span data-ttu-id="5c259-175">Database Mail 組態預存程序位於 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5c259-175">Database Mail configuration stored procedures are located in the **msdb** database.</span></span>  
  
 <span data-ttu-id="5c259-176">下表列出用來設定和管理 Database Mail 的預存程序。</span><span class="sxs-lookup"><span data-stu-id="5c259-176">The following tables list the stored procedures used for configuring and managing Database Mail.</span></span>  
  
### <a name="database-mail-settings"></a><span data-ttu-id="5c259-177">Database Mail 設定</span><span class="sxs-lookup"><span data-stu-id="5c259-177">Database Mail Settings</span></span>  
  
|<span data-ttu-id="5c259-178">名稱</span><span class="sxs-lookup"><span data-stu-id="5c259-178">Name</span></span>|<span data-ttu-id="5c259-179">描述</span><span class="sxs-lookup"><span data-stu-id="5c259-179">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="5c259-180">sysmail_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-180">sysmail_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|<span data-ttu-id="5c259-181">變更 Database Mail 的組態設定。</span><span class="sxs-lookup"><span data-stu-id="5c259-181">Changes configuration settings for Database Mail.</span></span>|  
|[<span data-ttu-id="5c259-182">sysmail_help_configure_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-182">sysmail_help_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql)|<span data-ttu-id="5c259-183">顯示 Database Mail 的組態設定。</span><span class="sxs-lookup"><span data-stu-id="5c259-183">Displays configuration settings for Database Mail.</span></span>|  
  
### <a name="accounts-and-profiles"></a><span data-ttu-id="5c259-184">帳戶與設定檔</span><span class="sxs-lookup"><span data-stu-id="5c259-184">Accounts and Profiles</span></span>  
  
|<span data-ttu-id="5c259-185">名稱</span><span class="sxs-lookup"><span data-stu-id="5c259-185">Name</span></span>|<span data-ttu-id="5c259-186">描述</span><span class="sxs-lookup"><span data-stu-id="5c259-186">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="5c259-187">sysmail_add_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-187">sysmail_add_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)|<span data-ttu-id="5c259-188">將郵件帳戶加入到 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="5c259-188">Adds a mail account to a Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-189">sysmail_delete_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-189">sysmail_delete_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-account-sp-transact-sql)|<span data-ttu-id="5c259-190">刪除 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-190">Deletes a Database Mail account.</span></span>|  
|[<span data-ttu-id="5c259-191">sysmail_delete_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-191">sysmail_delete_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql)|<span data-ttu-id="5c259-192">刪除 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="5c259-192">Deletes a Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql)|<span data-ttu-id="5c259-194">從 Database Mail 設定檔中移除帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-194">Removes an account from a Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-195">sysmail_help_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-195">sysmail_help_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql)|<span data-ttu-id="5c259-196">列出 Database Mail 帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-196">Lists information about Database Mail accounts.</span></span>|  
|[<span data-ttu-id="5c259-197">sysmail_help_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-197">sysmail_help_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql)|<span data-ttu-id="5c259-198">列出一或多個 Database Mail 設定檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-198">Lists information about one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="5c259-199">sysmail_help_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-199">sysmail_help_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql)|<span data-ttu-id="5c259-200">列出與一個或多個 Database Mail 設定檔相關聯的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c259-200">Lists the accounts associated with one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="5c259-201">sysmail_update_account_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-201">sysmail_update_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-account-sp-transact-sql)|<span data-ttu-id="5c259-202">更新現有 Database Mail 帳戶的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-202">Updates the information in an existing Database Mail account.</span></span>|  
|[<span data-ttu-id="5c259-203">sysmail_update_profile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-203">sysmail_update_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profile-sp-transact-sql)|<span data-ttu-id="5c259-204">變更 Database Mail 設定檔的描述或名稱。</span><span class="sxs-lookup"><span data-stu-id="5c259-204">Changes the description or name of a Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-205">sysmail_update_profileaccount_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-205">sysmail_update_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql)|<span data-ttu-id="5c259-206">更新 Database Mail 設定檔內的帳戶序號。</span><span class="sxs-lookup"><span data-stu-id="5c259-206">Updates the sequence number of an account within a Database Mail profile.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="5c259-207">安全性</span><span class="sxs-lookup"><span data-stu-id="5c259-207">Security</span></span>  
  
|<span data-ttu-id="5c259-208">名稱</span><span class="sxs-lookup"><span data-stu-id="5c259-208">Name</span></span>|<span data-ttu-id="5c259-209">描述</span><span class="sxs-lookup"><span data-stu-id="5c259-209">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="5c259-210">sysmail_add_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-210">sysmail_add_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)|<span data-ttu-id="5c259-211">授與資料庫主體使用 Database Mail 設定檔的權限。</span><span class="sxs-lookup"><span data-stu-id="5c259-211">Grants permission for a database principal to use a Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-principalprofile-sp-transact-sql)|<span data-ttu-id="5c259-213">移除資料庫使用者使用公用或私人 Database Mail 設定檔的權限。</span><span class="sxs-lookup"><span data-stu-id="5c259-213">Removes permission for a database user to use a public or private Database Mail profile.</span></span>|  
|[<span data-ttu-id="5c259-214">sysmail_help_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-214">sysmail_help_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql)|<span data-ttu-id="5c259-215">列出指定資料庫使用者的 Database Mail 設定檔資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-215">Lists Database Mail profile information for a given database user.</span></span>|  
|[<span data-ttu-id="5c259-216">sysmail_update_principalprofile_sp (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5c259-216">sysmail_update_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-principalprofile-sp-transact-sql)|<span data-ttu-id="5c259-217">更新指定資料庫使用者的權限資訊。</span><span class="sxs-lookup"><span data-stu-id="5c259-217">Updates the permission information for a given database user.</span></span>|  
  
### <a name="system-state"></a><span data-ttu-id="5c259-218">系統狀態</span><span class="sxs-lookup"><span data-stu-id="5c259-218">System State</span></span>  
  
|<span data-ttu-id="5c259-219">名稱</span><span class="sxs-lookup"><span data-stu-id="5c259-219">Name</span></span>|<span data-ttu-id="5c259-220">描述</span><span class="sxs-lookup"><span data-stu-id="5c259-220">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="5c259-221">sysmail_start_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c259-221">sysmail_start_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|<span data-ttu-id="5c259-222">啟動 Database Mail 外部程式，以及關聯的 SQL Service Broker 佇列。</span><span class="sxs-lookup"><span data-stu-id="5c259-222">Starts the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="5c259-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c259-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|<span data-ttu-id="5c259-224">停止 Database Mail 外部程式，以及關聯的 SQL Service Broker 佇列。</span><span class="sxs-lookup"><span data-stu-id="5c259-224">Stops the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="5c259-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c259-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|<span data-ttu-id="5c259-226">指示 Database Mail 是否已啟動。</span><span class="sxs-lookup"><span data-stu-id="5c259-226">Indicates if Database Mail is started.</span></span>|  
  
##  <a name="additional-references"></a><a name="RelatedContent"></a> <span data-ttu-id="5c259-227">其他參考</span><span class="sxs-lookup"><span data-stu-id="5c259-227">Additional References</span></span>  
  
-   [<span data-ttu-id="5c259-228">Database Mail 記錄與稽核</span><span class="sxs-lookup"><span data-stu-id="5c259-228">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
  
