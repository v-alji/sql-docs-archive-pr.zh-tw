---
title: 建立 Database Mail 設定檔 | Microsoft 文件
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], public profiles
- profiles [SQL Server], Database Mail
- public profiles [Database Mail]
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0453d495c90c1e599bfc7777b4899f30e6659c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594102"
---
# <a name="create-a-database-mail-profile"></a><span data-ttu-id="77943-102">建立 Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="77943-102">Create a Database Mail Profile</span></span>
  <span data-ttu-id="77943-103">您可以使用 [Database Mail 組態精靈]  或 [!INCLUDE[tsql](../../includes/tsql-md.md)]，建立 Database Mail 公用和私人設定檔。</span><span class="sxs-lookup"><span data-stu-id="77943-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create Database Mail public and private profiles.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="77943-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="77943-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="77943-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="77943-105">Prerequisites</span></span>  
 <span data-ttu-id="77943-106">替該設定檔建立一個或多個 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="77943-106">Create one or more Database Mail accounts for the profile.</span></span> <span data-ttu-id="77943-107">如需建立 Database Mail 帳戶的詳細資訊，請參閱 [建立 Database Mail 帳戶](create-a-database-mail-account.md)。</span><span class="sxs-lookup"><span data-stu-id="77943-107">For more information about creating Database Mail accounts, see [Create a Database Mail Account](create-a-database-mail-account.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="77943-108">Security</span><span class="sxs-lookup"><span data-stu-id="77943-108">Security</span></span>  
 <span data-ttu-id="77943-109">公用設定檔可以讓任何可存取 **msdb** 資料庫的使用者使用該設定檔來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="77943-109">A public profile allows any user with access to the **msdb** database to send e-mail using that profile.</span></span> <span data-ttu-id="77943-110">使用者或角色可以使用私人設定檔。</span><span class="sxs-lookup"><span data-stu-id="77943-110">A private profile can be used by a user or by a role.</span></span> <span data-ttu-id="77943-111">為角色授與設定檔的存取權限時，會建立能夠更輕鬆維護的架構。</span><span class="sxs-lookup"><span data-stu-id="77943-111">Granting roles access to profiles creates a more easily maintained architecture.</span></span> <span data-ttu-id="77943-112">您必須是 **msdb** 資料庫中之 **DatabaseMailUserRole** 的成員，而且至少可以存取一個 Database Mail 設定檔，才能傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="77943-112">To send mail you must be a member of the **DatabaseMailUserRole** in the **msdb** database, and have access to at least one Database Mail profile.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="77943-113">權限</span><span class="sxs-lookup"><span data-stu-id="77943-113">Permissions</span></span>  
 <span data-ttu-id="77943-114">建立設定檔帳戶以及執行預存程序的使用者，應該是系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="77943-114">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  

  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="77943-115">使用 Database Mail 組態精靈</span><span class="sxs-lookup"><span data-stu-id="77943-115">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="77943-116">**建立 Database Mail 設定檔**</span><span class="sxs-lookup"><span data-stu-id="77943-116">**To Create a Database Mail profile**</span></span>  
  
-   <span data-ttu-id="77943-117">在 [物件總管] 中，連接到想要在其上設定 Database Mail 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="77943-117">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="77943-118">展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="77943-118">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="77943-119">按兩下 Database Mail，開啟 [Database Mail 組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="77943-119">Double click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="77943-120">在 [**選取**設定工作] 頁面上，選取 [**管理 Database Mail 帳戶和設定檔**] 選項，然後按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="77943-120">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option and click **Next**.</span></span>  
  
-   <span data-ttu-id="77943-121">在 [管理設定檔和帳戶]\*\*\*\* 頁面上，選取 [建立新設定檔]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-121">On the **Manage Profiles and Accounts** page, select **Create a new profile** option, and click **Next**.</span></span>  
  
-   <span data-ttu-id="77943-122">在 [新增設定檔]\*\*\*\* 頁面上，指定設定檔名稱、描述並新增要併入設定檔中的帳戶，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-122">On the **New Profile** page, specify the Profile name, Description and add accounts to be included in the profile, and click **Next**.</span></span>  
  
-   <span data-ttu-id="77943-123">在 [完成精靈]\*\*\*\* 頁面上，檢閱要執行的動作，然後按一下 [完成]\*\*\*\* 完成新設定檔的建立。</span><span class="sxs-lookup"><span data-stu-id="77943-123">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new profile.</span></span>  
  
-   <span data-ttu-id="77943-124">**若要設定 Database Mail 私人設定檔：**</span><span class="sxs-lookup"><span data-stu-id="77943-124">**To configure a Database Mail private profile:**</span></span>  
  
    -   <span data-ttu-id="77943-125">開啟 [Database Mail 組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="77943-125">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="77943-126">在 [選取組態工作]\*\*\*\* 頁面上，選取 [管理 Database Mail 帳戶和設定檔]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-126">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-127">在 [管理設定檔和帳戶]\*\*\*\* 頁面上，選取 [管理設定檔安全性]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-127">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-128">在 [私人設定檔]\*\*\*\* 索引標籤中，選取想要設定之設定檔的核取方塊，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-128">In the **Private Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-129">在 [完成精靈]\*\*\*\* 頁面上，檢閱要執行的動作，然後按一下 [完成]\*\*\*\* 完成設定檔的設定。</span><span class="sxs-lookup"><span data-stu-id="77943-129">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  
-   <span data-ttu-id="77943-130">**若要設定 Database Mail 公用設定檔：**</span><span class="sxs-lookup"><span data-stu-id="77943-130">**To configure a Database Mail public profile:**</span></span>  
  
    -   <span data-ttu-id="77943-131">開啟 [Database Mail 組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="77943-131">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="77943-132">在 [選取組態工作]\*\*\*\* 頁面上，選取 [管理 Database Mail 帳戶和設定檔]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-132">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-133">在 [管理設定檔和帳戶]\*\*\*\* 頁面上，選取 [管理設定檔安全性]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-133">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-134">在 [公用設定檔]\*\*\*\* 索引標籤中，選取想要設定之設定檔的核取方塊，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77943-134">In the **Public Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="77943-135">在 [完成精靈]\*\*\*\* 頁面上，檢閱要執行的動作，然後按一下 [完成]\*\*\*\* 完成設定檔的設定。</span><span class="sxs-lookup"><span data-stu-id="77943-135">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  

  
## <a name="using-transact-sql"></a><span data-ttu-id="77943-136">使用 TRANSACT-SQL</span><span class="sxs-lookup"><span data-stu-id="77943-136">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-database-mail-private-profile"></a><a name="PrivateProfile"></a><span data-ttu-id="77943-137">建立 Database Mail 私人設定檔</span><span class="sxs-lookup"><span data-stu-id="77943-137">To Create a Database Mail private profile</span></span>  
  
-   <span data-ttu-id="77943-138">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="77943-138">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="77943-139">若要建立新的設定檔，請執行系統預存程序 [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-139">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="77943-141">*@profile_name*= '*設定檔名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-141">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="77943-142">*@description*= '*描述 '*</span><span class="sxs-lookup"><span data-stu-id="77943-142">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="77943-143">其中， *@profile_name* 是設定檔的名稱，而 *@description* 是設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="77943-143">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="77943-144">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="77943-144">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="77943-145">針對每個帳戶，執行預存程序 [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-145">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="77943-147">*@profile_name*= '*設定檔的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-147">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="77943-148">*@account_name*= '*帳戶的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-148">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="77943-149">*@sequence_number*= '*帳戶在設定檔內的序號。*</span><span class="sxs-lookup"><span data-stu-id="77943-149">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="77943-150">'</span><span class="sxs-lookup"><span data-stu-id="77943-150">'</span></span>  
  
     <span data-ttu-id="77943-151">其中， *@profile_name* 是設定檔的名稱，而 *@account_name* 是要新增至設定檔的帳戶名稱，可 *@sequence_number* 決定帳戶在設定檔中的使用順序。</span><span class="sxs-lookup"><span data-stu-id="77943-151">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="77943-152">針對使用此設定檔傳送郵件的每個資料庫角色或使用者，授與設定檔的存取權。</span><span class="sxs-lookup"><span data-stu-id="77943-152">For each database role or user that will send mail using this profile, grant access to the profile.</span></span> <span data-ttu-id="77943-153">作法是執行預存程序 [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-153">To do this, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="77943-155">*@profile_name*= '*設定檔的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-155">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="77943-156">*@ principal_name* = '*資料庫使用者或角色的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-156">*@ principal_name* = '*Name of the database user or role*'</span></span>  
  
     <span data-ttu-id="77943-157">*@is_default*= '*預設設定檔狀態*'</span><span class="sxs-lookup"><span data-stu-id="77943-157">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="77943-158">其中， *@profile_name* 是設定檔的名稱，而 *@principal_name* 是資料庫使用者或角色的名稱，可 *@is_default* 決定此設定檔是否為資料庫使用者或角色的預設值。</span><span class="sxs-lookup"><span data-stu-id="77943-158">where *@profile_name* is the name of the profile, and *@principal_name* is the name of the database user or role, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="77943-159">下列範例會建立 Database Mail 帳戶、建立 Database Mail 私人設定檔，然後將帳戶加入設定檔，並將設定檔的存取權授與 **msdb** 資料庫中的 **DBMailUsers** 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="77943-159">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants access to the profile to the **DBMailUsers** database role in the **msdb** database.</span></span>  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
 
  
###  <a name="to-create-a-database-mail-public-profile"></a><a name="PublicProfile"></a> <span data-ttu-id="77943-160">建立 Database Mail 公用設定檔</span><span class="sxs-lookup"><span data-stu-id="77943-160">To Create a Database Mail public profile</span></span>  
  
-   <span data-ttu-id="77943-161">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="77943-161">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="77943-162">若要建立新的設定檔，請執行系統預存程序 [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-162">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="77943-164">*@profile_name*= '*設定檔名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-164">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="77943-165">*@description*= '*描述 '*</span><span class="sxs-lookup"><span data-stu-id="77943-165">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="77943-166">其中， *@profile_name* 是設定檔的名稱，而 *@description* 是設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="77943-166">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="77943-167">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="77943-167">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="77943-168">針對每個帳戶，執行預存程序 [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-168">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="77943-170">*@profile_name*= '*設定檔的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-170">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="77943-171">*@account_name*= '*帳戶的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-171">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="77943-172">*@sequence_number*= '*帳戶在設定檔內的序號。*</span><span class="sxs-lookup"><span data-stu-id="77943-172">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="77943-173">'</span><span class="sxs-lookup"><span data-stu-id="77943-173">'</span></span>  
  
     <span data-ttu-id="77943-174">其中， *@profile_name* 是設定檔的名稱，而 *@account_name* 是要新增至設定檔的帳戶名稱，可 *@sequence_number* 決定帳戶在設定檔中的使用順序。</span><span class="sxs-lookup"><span data-stu-id="77943-174">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="77943-175">若要授與公用存取權，請執行預存程序 [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77943-175">To grant public access, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="77943-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="77943-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="77943-177">*@profile_name*= '*設定檔的名稱*'</span><span class="sxs-lookup"><span data-stu-id="77943-177">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="77943-178">*@ principal_name* = '**public** 或 **0**'</span><span class="sxs-lookup"><span data-stu-id="77943-178">*@ principal_name* = '**public** or **0**'</span></span>  
  
     <span data-ttu-id="77943-179">*@is_default*= '*預設設定檔狀態*'</span><span class="sxs-lookup"><span data-stu-id="77943-179">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="77943-180">其中， *@profile_name* 是設定檔的名稱，而 *@principal_name* 表示這是公用設定檔，可 *@is_default* 決定此設定檔是否為資料庫使用者或角色的預設值。</span><span class="sxs-lookup"><span data-stu-id="77943-180">where *@profile_name* is the name of the profile, and *@principal_name* to indicate this is a public profile, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="77943-181">下列範例會建立 Database Mail 帳戶、建立 Database Mail 私人設定檔，然後將帳戶加入設定檔，並授與設定檔的公用存取權。</span><span class="sxs-lookup"><span data-stu-id="77943-181">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants public access to the profile.</span></span>  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  

  
  
