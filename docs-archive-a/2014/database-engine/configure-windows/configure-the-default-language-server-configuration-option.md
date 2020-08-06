---
title: 設定 default language 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b0e62fef112dad2c6c307946bc720adf1f14d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708613"
---
# <a name="configure-the-default-language-server-configuration-option"></a><span data-ttu-id="2e8bb-102">設定 default language 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="2e8bb-102">Configure the default language Server Configuration Option</span></span>
  <span data-ttu-id="2e8bb-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] default language [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-103">This topic describes how to configure the **default language** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2e8bb-104">**default language** 選項會指定所有新建登入的預設語言。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-104">The **default language** option specifies the default language for all newly created logins.</span></span> <span data-ttu-id="2e8bb-105">若要設定預設語言，請指定所需語言的 **langid** 值。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-105">To set default language, specify the **langid** value of the language you want.</span></span> <span data-ttu-id="2e8bb-106">**langid** 值可透過查詢 **sys.syslanguages** 相容性檢視來取得。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-106">The **langid** value can be obtained by querying the **sys.syslanguages** compatibility view.</span></span>  
  
 <span data-ttu-id="2e8bb-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2e8bb-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e8bb-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2e8bb-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e8bb-109">建議</span><span class="sxs-lookup"><span data-stu-id="2e8bb-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2e8bb-110">安全性</span><span class="sxs-lookup"><span data-stu-id="2e8bb-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2e8bb-111">**使用下列方法設定 default language 選項：**</span><span class="sxs-lookup"><span data-stu-id="2e8bb-111">**To configure the default language option, using:**</span></span>  
  
     [<span data-ttu-id="2e8bb-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e8bb-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2e8bb-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e8bb-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2e8bb-114">**後續操作：** [設定預設語言選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2e8bb-114">**Follow Up:**  [After you configure the default language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e8bb-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="2e8bb-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2e8bb-116">建議</span><span class="sxs-lookup"><span data-stu-id="2e8bb-116">Recommendations</span></span>  
  
-   <span data-ttu-id="2e8bb-117">使用 CREATE LOGIN 或 ALTER LOGIN 可覆寫登入的預設語言。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-117">The default language for a login can be overridden by using CREATE LOGIN or ALTER LOGIN.</span></span> <span data-ttu-id="2e8bb-118">除非使用開放式資料庫連接 (Open Database Connectivity，ODBC) 或 OLE DB API 分別覆寫每個工作階段的語言，否則工作階段的預設語言就是該工作階段的登入語言。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-118">The default language for a session is the language for that session's login, unless overridden on a per-session basis by using the Open Database Connectivity (ODBC) or OLE DB APIs.</span></span> <span data-ttu-id="2e8bb-119">請注意，您只能將 **default language** 選項設為 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) 中定義的語言識別碼 (0-32)。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-119">Note that you can only set the **default language** option to a language ID defined in [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0-32).</span></span> <span data-ttu-id="2e8bb-120">使用自主資料庫時，可以使用 CREATE DATABASE 或 ALTER DATABASE 為資料庫設定預設語言，以及使用 CREATE USER 或 ALTER USER 為自主資料庫使用者設定預設語言。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-120">When you are using contained databases, a default language can be set for a database by using CREATE DATABASE or ALTER DATABASE, and for contained database users by using CREATE USER or ALTER USER.</span></span> <span data-ttu-id="2e8bb-121">在自主資料庫中設定預設語言會接受 **langid** 值、語言名稱或語言別名，如 **sys.syslanguages**中所列。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-121">Setting default languages in a contained database accepts **langid** value, the language name, or a language alias as listed in **sys.syslanguages**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2e8bb-122">Security</span><span class="sxs-lookup"><span data-stu-id="2e8bb-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2e8bb-123">權限</span><span class="sxs-lookup"><span data-stu-id="2e8bb-123">Permissions</span></span>  
 <span data-ttu-id="2e8bb-124">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="2e8bb-125">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="2e8bb-126">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e8bb-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e8bb-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="2e8bb-128">設定 default language 選項</span><span class="sxs-lookup"><span data-stu-id="2e8bb-128">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="2e8bb-129">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2e8bb-130">按一下 **[其他伺服器設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="2e8bb-131">在 **[使用者的預設語言]** 方塊中，選擇 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 應以哪種語言顯示系統訊息。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-131">In the **Default language for users** box, choose the language in which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should display system messages.</span></span>  
  
     <span data-ttu-id="2e8bb-132">預設語言為英文。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-132">The default language is English.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2e8bb-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e8bb-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-language-option"></a><span data-ttu-id="2e8bb-134">設定 default language 選項</span><span class="sxs-lookup"><span data-stu-id="2e8bb-134">To configure the default language option</span></span>  
  
1.  <span data-ttu-id="2e8bb-135">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2e8bb-136">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2e8bb-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2e8bb-138">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `default language` 選項設定為法文 (`2`)。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `default language` option to French (`2`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 <span data-ttu-id="2e8bb-139">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="2e8bb-140">後續操作：設定預設語言選項之後</span><span class="sxs-lookup"><span data-stu-id="2e8bb-140">Follow Up: After you configure the default language option</span></span>  
 <span data-ttu-id="2e8bb-141">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="2e8bb-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8bb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e8bb-142">See Also</span></span>  
 <span data-ttu-id="2e8bb-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-143">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-144">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-145">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-146">[ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-147">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-148">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2e8bb-150">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2e8bb-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="2e8bb-151">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e8bb-151">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
