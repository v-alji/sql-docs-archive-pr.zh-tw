---
title: 設定 user connections 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- simultaneous connections [SQL Server]
- user connections option [SQL Server]
- users [SQL Server], simultaneous connections
- maximum number of simultaneous user connections
- connections [SQL Server], simultaneous
ms.assetid: 53beee6e-59fe-4276-9abb-8f1cec2a3508
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fbb4a17de131c128b5b1bb7cfb35a33b9d0037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585585"
---
# <a name="configure-the-user-connections-server-configuration-option"></a><span data-ttu-id="26094-102">設定 user connections 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="26094-102">Configure the user connections Server Configuration Option</span></span>
  <span data-ttu-id="26094-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user connections [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="26094-103">This topic describes how to set the **user connections** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="26094-104">**user connections** 選項會指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上可同時連接的使用者數目上限。</span><span class="sxs-lookup"><span data-stu-id="26094-104">The **user connections** option specifies the maximum number of simultaneous user connections that are allowed on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="26094-105">實際允許的使用者連接數也取決於您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本，以及應用程式的限制或應用程式和硬體的限制而定。</span><span class="sxs-lookup"><span data-stu-id="26094-105">The actual number of user connections allowed also depends on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using, and also the limits of your application or applications and hardware.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="26094-106">最多允許 32,767 個使用者連接。</span><span class="sxs-lookup"><span data-stu-id="26094-106">allows a maximum of 32,767 user connections.</span></span> <span data-ttu-id="26094-107">因為 **user connections** 是動態的 (自我設定的) 選項，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會視需要自動調整最大使用者連接數，最多調整到允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="26094-107">Because **user connections** is a dynamic (self-configuring) option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adjusts the maximum number of user connections automatically as needed, up to the maximum value allowable.</span></span> <span data-ttu-id="26094-108">例如，如果只有 10 個使用者登入，就配置 10 個使用者連線物件。</span><span class="sxs-lookup"><span data-stu-id="26094-108">For example, if only 10 users are logged in, 10 user connection objects are allocated.</span></span> <span data-ttu-id="26094-109">在大部分情況下，不需要變更這個選項的值。</span><span class="sxs-lookup"><span data-stu-id="26094-109">In most cases, you do not have to change the value for this option.</span></span> <span data-ttu-id="26094-110">預設值為 0，表示允許最大量 (32,767) 的使用者連接數。</span><span class="sxs-lookup"><span data-stu-id="26094-110">The default is 0, which means that the maximum (32,767) user connections are allowed.</span></span>  
  
 <span data-ttu-id="26094-111">若要判斷系統允許的最大使用者連接數目，您可以執行 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 或查詢 [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="26094-111">To determine the maximum number of user connections that your system allows, you can execute [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) or query the [sys.configuration](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="26094-112">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="26094-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="26094-113">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="26094-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="26094-114">建議</span><span class="sxs-lookup"><span data-stu-id="26094-114">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="26094-115">安全性</span><span class="sxs-lookup"><span data-stu-id="26094-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="26094-116">**使用下列方法設定 user connections 選項：**</span><span class="sxs-lookup"><span data-stu-id="26094-116">**To configure the user connections option, using:**</span></span>  
  
     [<span data-ttu-id="26094-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26094-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="26094-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="26094-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="26094-119">**後續操作：** [設定使用者連線選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="26094-119">**Follow Up:**  [After you configure the user connections option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="26094-120">開始之前</span><span class="sxs-lookup"><span data-stu-id="26094-120">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="26094-121">建議</span><span class="sxs-lookup"><span data-stu-id="26094-121">Recommendations</span></span>  
  
-   <span data-ttu-id="26094-122">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="26094-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="26094-123">使用 **user connections** 選項有助於避免因並行連接過多，而導致伺服器超過負載。</span><span class="sxs-lookup"><span data-stu-id="26094-123">Using the **user connections** option helps avoid overloading the server with too many concurrent connections.</span></span> <span data-ttu-id="26094-124">您可以根據系統與使用者需求估計連接數。</span><span class="sxs-lookup"><span data-stu-id="26094-124">You can estimate the number of connections based on system and user requirements.</span></span> <span data-ttu-id="26094-125">例如，在有許多使用者的系統上，通常不會每個使用者各要求一個唯一的連接。</span><span class="sxs-lookup"><span data-stu-id="26094-125">For example, on a system with many users, each user would not usually require a unique connection.</span></span> <span data-ttu-id="26094-126">連接可以由使用者共用。</span><span class="sxs-lookup"><span data-stu-id="26094-126">Connections can be shared among users.</span></span> <span data-ttu-id="26094-127">執行 OLE DB 應用程式的使用者，對每個開啟的連接物件都必須各有一個連接；執行開放式資料庫連接 (ODBC) 應用程式的使用者，對應用程式中的每個使用中連接控制代碼都必須各有一個連接；而執行 DB-Library 應用程式的使用者，則對呼叫 DB-Library **dbopen** 函數的每個啟動處理序都必須各有一個連接。</span><span class="sxs-lookup"><span data-stu-id="26094-127">Users running OLE DB applications need a connection for each open connection object, users running Open Database Connectivity (ODBC) applications need a connection for each active connection handle in the application, and users running DB-Library applications need one connection for each process started that calls the DB-Library **dbopen** function.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="26094-128">如果必須使用這個選項，請不要將這個值設得太大，因為每個連接不論使用與否，都會造成額外負擔。</span><span class="sxs-lookup"><span data-stu-id="26094-128">If you must use this option, do not set the value too high, because each connection has overhead regardless of whether the connection is being used.</span></span> <span data-ttu-id="26094-129">如果超過最大使用者連接數，就會收到錯誤訊息，然後要等到可以使用另一個連接後，才能再繼續進行連接。</span><span class="sxs-lookup"><span data-stu-id="26094-129">If you exceed the maximum number of user connections, you receive an error message and are not able to connect until another connection becomes available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="26094-130">Security</span><span class="sxs-lookup"><span data-stu-id="26094-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="26094-131">權限</span><span class="sxs-lookup"><span data-stu-id="26094-131">Permissions</span></span>  
 <span data-ttu-id="26094-132">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="26094-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="26094-133">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="26094-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="26094-134">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="26094-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="26094-135">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="26094-135">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="26094-136">設定 user connections 選項</span><span class="sxs-lookup"><span data-stu-id="26094-136">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="26094-137">在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="26094-137">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="26094-138">按一下 **[連接]** 節點。</span><span class="sxs-lookup"><span data-stu-id="26094-138">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="26094-139">在 **[連接]** 下的 **[並行連接的最大數目]** 方塊中，輸入或選取 0 至 32767 之間的值，以設定可同時連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的最大使用者數目。</span><span class="sxs-lookup"><span data-stu-id="26094-139">Under **Connections**, in the **Max number of concurrent connections** box, type or select a value from 0 through 32767 to set the maximum number of users that are allowed to connect simultaneously to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="26094-140">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26094-140">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="26094-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="26094-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-connections-option"></a><span data-ttu-id="26094-142">設定 user connections 選項</span><span class="sxs-lookup"><span data-stu-id="26094-142">To configure the user connections option</span></span>  
  
1.  <span data-ttu-id="26094-143">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26094-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="26094-144">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="26094-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="26094-145">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="26094-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="26094-146">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 以將 `user connections` 選項的值設定為 `325` 位使用者。</span><span class="sxs-lookup"><span data-stu-id="26094-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the value of the `user connections` option to `325` users.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'user connections', 325 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="26094-147">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="26094-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-user-connections-option"></a><a name="FollowUp"></a> <span data-ttu-id="26094-148">後續操作：設定使用者連線選項之後</span><span class="sxs-lookup"><span data-stu-id="26094-148">Follow Up: After you configure the user connections option</span></span>  
 <span data-ttu-id="26094-149">伺服器必須重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="26094-149">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26094-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26094-150">See Also</span></span>  
 <span data-ttu-id="26094-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26094-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="26094-152">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26094-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="26094-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26094-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
