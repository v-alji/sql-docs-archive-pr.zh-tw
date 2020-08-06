---
title: 建立 Database Mail 帳戶| Microsoft 文件
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec7d1c9147998b5a19cc0e6af13220bd64e165fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594103"
---
# <a name="create-a-database-mail-account"></a><span data-ttu-id="a0d87-102">建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="a0d87-102">Create a Database Mail Account</span></span>
  <span data-ttu-id="a0d87-103">您可以使用 **「Database Mail 組態精靈」** 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，建立 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0d87-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a Database Mail account.</span></span>  
  
-   <span data-ttu-id="a0d87-104">**開始之前：** [必要條件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="a0d87-104">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="a0d87-105">**使用下列項目建立 Database Mail 帳戶：** [Database Mail 設定精靈](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="a0d87-105">**To Create a Database Mail Account, using:**  [Database Mail Configuration Wizard](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="a0d87-106">**後續操作：** [設定 Database Mail 的後續步驟](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a0d87-106">**Follow Up:**  [Next Steps to Configure the Database Mail](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a0d87-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="a0d87-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a0d87-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="a0d87-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="a0d87-109">判斷您用於傳送電子郵件之 Simple Mail Transfer Protocol (SMTP) 伺服器的伺服器名稱和通訊埠編號。如果 SMTP 伺服器需要驗證，請判斷 SMTP 伺服器的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a0d87-109">Determine the server name and port number for the Simple Mail Transfer Protocol (SMTP) server you use to send e-mail.If the SMTP server requires authentication, determine the user name and password for the SMTP server.</span></span>  
  
-   <span data-ttu-id="a0d87-110">(選擇性) 您也可以指定伺服器的類型和伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="a0d87-110">Optionally, you may also specify the type of the server and the port number for the server.</span></span> <span data-ttu-id="a0d87-111">外寄郵件的伺服器類型一律為 'SMTP'。</span><span class="sxs-lookup"><span data-stu-id="a0d87-111">The server type is always 'SMTP' for outgoing mail.</span></span> <span data-ttu-id="a0d87-112">大部分 SMTP 伺服器會使用通訊埠 25 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a0d87-112">Most SMTP servers use port 25, the default.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a0d87-113">使用 Database Mail 組態精靈</span><span class="sxs-lookup"><span data-stu-id="a0d87-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="a0d87-114">**使用精靈建立 Database Mail 帳戶**</span><span class="sxs-lookup"><span data-stu-id="a0d87-114">**To create a Database Mail account using a Wizard**</span></span>  
  
-   <span data-ttu-id="a0d87-115">在 [物件總管] 中，連接到想要在其上設定 Database Mail 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="a0d87-115">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="a0d87-116">展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a0d87-116">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="a0d87-117">按兩下 Database Mail，開啟 [Database Mail 組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="a0d87-117">Double Click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="a0d87-118">在 **[選取組態工作]** 頁面上，選取 **[管理 Database Mail 帳戶和設定檔]** ，並按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="a0d87-118">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles**, and click **Next**.</span></span>  
  
-   <span data-ttu-id="a0d87-119">在 **[管理設定檔和帳戶]** 頁面上，選取 **[建立新帳戶]** ，並按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="a0d87-119">On the **Manage Profiles and Accounts** page, select **Create a new account** and click **Next**.</span></span>  
  
-   <span data-ttu-id="a0d87-120">在 **[新增帳戶]** 頁面上，指定帳戶名稱、描述、郵件伺服器資訊和驗證類型。</span><span class="sxs-lookup"><span data-stu-id="a0d87-120">On the **New Account** page, specify the account name, description, mail server information, and authentication type.</span></span> <span data-ttu-id="a0d87-121">按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="a0d87-121">Click **Next**</span></span>  
  
-   <span data-ttu-id="a0d87-122">在 **[完成精靈]** 頁面上，檢閱要執行的動作，並按一下 **[完成]** 完成新帳戶的建立。</span><span class="sxs-lookup"><span data-stu-id="a0d87-122">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new account.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a0d87-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0d87-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="a0d87-124">**使用 Transact-SQL 建立 Database Mail 帳戶**</span><span class="sxs-lookup"><span data-stu-id="a0d87-124">**To Create a Database Mail account using Transact-SQL**</span></span>  
  
 <span data-ttu-id="a0d87-125">執行預存程序 **msdb.dbo.sysmail_add_account_sp** 來建立帳戶，並且指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="a0d87-125">Execute the stored procedure **msdb.dbo.sysmail_add_account_sp** to create the account and specify the following information:</span></span>  
  
-   <span data-ttu-id="a0d87-126">要建立的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d87-126">The name of the account to create.</span></span>  
  
-   <span data-ttu-id="a0d87-127">帳戶的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="a0d87-127">An optional description of the account.</span></span>  
  
-   <span data-ttu-id="a0d87-128">要顯示於外寄電子郵件訊息的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a0d87-128">The e-mail address to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="a0d87-129">要顯示於外寄電子郵件訊息的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d87-129">The display name to show on outgoing e-mail messages.</span></span>  
  
-   <span data-ttu-id="a0d87-130">SMTP 伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d87-130">The server name of the SMTP server.</span></span>  
  
-   <span data-ttu-id="a0d87-131">要用於登入 SMTP 伺服器的使用者名稱 (如果 SMTP 伺服器需要驗證的話)。</span><span class="sxs-lookup"><span data-stu-id="a0d87-131">The user name to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
-   <span data-ttu-id="a0d87-132">要用於登入 SMTP 伺服器的密碼 (如果 SMTP 伺服器需要驗證的話)。</span><span class="sxs-lookup"><span data-stu-id="a0d87-132">The password to use to log on to the SMTP server, if the SMTP server requires authentication.</span></span>  
  
 <span data-ttu-id="a0d87-133">下列範例會建立新的 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0d87-133">The following example creates a new Database Mail account.</span></span>  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="follow-up-next-steps-to-configuring-the-database-mail"></a><a name="FollowUp"></a> <span data-ttu-id="a0d87-134">後續操作：設定 Database Mail 的後續步驟</span><span class="sxs-lookup"><span data-stu-id="a0d87-134">Follow Up: Next Steps to Configuring the Database Mail</span></span>  
  
-   [<span data-ttu-id="a0d87-135">建立 Database Mail 設定檔</span><span class="sxs-lookup"><span data-stu-id="a0d87-135">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)  
  
  
