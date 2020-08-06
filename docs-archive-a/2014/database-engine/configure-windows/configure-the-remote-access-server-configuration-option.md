---
title: 設定 remote access 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eef18ec48ede59544b13545e49dc105909cfac16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592235"
---
# <a name="configure-the-remote-access-server-configuration-option"></a><span data-ttu-id="08d58-102">設定 remote access 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="08d58-102">Configure the remote access Server Configuration Option</span></span>
  <span data-ttu-id="08d58-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote access [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="08d58-103">This topic describes how to configure the **remote access** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="08d58-104">**remote access** 選項會控制本機或遠端伺服器 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的執行所在) 上執行的預存程序。</span><span class="sxs-lookup"><span data-stu-id="08d58-104">The **remote access** option controls the execution of stored procedures from local or remote servers on which instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are running.</span></span> <span data-ttu-id="08d58-105">這個選項的預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="08d58-105">This default value for this option is 1.</span></span> <span data-ttu-id="08d58-106">這會授與權限以從遠端伺服器執行本機預存程序，或從本機伺服器執行遠端預存程序。</span><span class="sxs-lookup"><span data-stu-id="08d58-106">This grants permission to run local stored procedures from remote servers or remote stored procedures from the local server.</span></span> <span data-ttu-id="08d58-107">若要防止在遠端伺服器上執行本機預存程序，或在本機伺服器上執行遠端預存程序，請將此選項設定為 0。</span><span class="sxs-lookup"><span data-stu-id="08d58-107">To prevent local stored procedures from being run from a remote server or remote stored procedures from being run on the local server, set the option to 0.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="08d58-108">請改用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="08d58-108">Use [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="08d58-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="08d58-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="08d58-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="08d58-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="08d58-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="08d58-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="08d58-112">安全性</span><span class="sxs-lookup"><span data-stu-id="08d58-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="08d58-113">**使用下列方法設定 remote access 選項：**</span><span class="sxs-lookup"><span data-stu-id="08d58-113">**To configure the remote access option, using:**</span></span>  
  
     [<span data-ttu-id="08d58-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="08d58-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="08d58-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="08d58-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="08d58-116">**後續操作：** [設定遠端存取選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="08d58-116">**Follow Up:**  [After you configure the remote access option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="08d58-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="08d58-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="08d58-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="08d58-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="08d58-119">[遠端存取] 選項只適用於透過 [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 新增的伺服器，且其包含回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="08d58-119">The **remote access** option only applies to servers that are added by using [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), and is included for backward compatibility.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="08d58-120">Security</span><span class="sxs-lookup"><span data-stu-id="08d58-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="08d58-121">權限</span><span class="sxs-lookup"><span data-stu-id="08d58-121">Permissions</span></span>  
 <span data-ttu-id="08d58-122">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="08d58-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="08d58-123">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="08d58-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="08d58-124">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="08d58-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="08d58-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="08d58-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="08d58-126">設定 remote access 選項</span><span class="sxs-lookup"><span data-stu-id="08d58-126">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="08d58-127">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="08d58-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="08d58-128">按一下 **[連接]** 節點。</span><span class="sxs-lookup"><span data-stu-id="08d58-128">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="08d58-129">在 **[遠端伺服器連接]** 下，選取或清除 **[允許此伺服器的遠端連接]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="08d58-129">Under **Remote server connections**, select or clear the **Allow remote connections to this server** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="08d58-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="08d58-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-access-option"></a><span data-ttu-id="08d58-131">設定 remote access 選項</span><span class="sxs-lookup"><span data-stu-id="08d58-131">To configure the remote access option</span></span>  
  
1.  <span data-ttu-id="08d58-132">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="08d58-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="08d58-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="08d58-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="08d58-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="08d58-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="08d58-135">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `remote access` 選項的值設定為 `0`。</span><span class="sxs-lookup"><span data-stu-id="08d58-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote access` option to `0`.</span></span>  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="08d58-136">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="08d58-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-access-option"></a><a name="FollowUp"></a> <span data-ttu-id="08d58-137">後續操作：設定遠端存取選項之後</span><span class="sxs-lookup"><span data-stu-id="08d58-137">Follow Up: After you configure the remote access option</span></span>  
 <span data-ttu-id="08d58-138">此設定在您重新啟動 SQL Server 後才會生效。</span><span class="sxs-lookup"><span data-stu-id="08d58-138">This setting does not take effect until you restart SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d58-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08d58-139">See Also</span></span>  
 <span data-ttu-id="08d58-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08d58-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="08d58-141">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="08d58-141">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="08d58-142">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08d58-142">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
