---
title: 設定 remote login timeout 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58b3405f9b0e51bd43edcaa31e84c8ebbcc48547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592232"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a><span data-ttu-id="1edbb-102">設定 remote login timeout 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="1edbb-102">Configure the remote login timeout Server Configuration Option</span></span>
  <span data-ttu-id="1edbb-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote login timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="1edbb-103">This topic describes how to configure the **remote login timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1edbb-104">**remote login timeout** 選項指定登入遠端伺服器的嘗試在傳回失敗前等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="1edbb-104">The **remote login timeout** option specifies the number of seconds to wait before returning from a failed attempt to log in to a remote server.</span></span> <span data-ttu-id="1edbb-105">例如，如果您嘗試登入遠端伺服器，而該伺服器已關機， **remote login timeout** 有助於確保在您的電腦停止嘗試登入前，您不必無限期等下去。</span><span class="sxs-lookup"><span data-stu-id="1edbb-105">For example, if you are trying to log in to a remote server and that server is down, **remote login timeout** helps make sure that you do not have to wait indefinitely before your computer stops trying to log in.</span></span> <span data-ttu-id="1edbb-106">這個選項的預設值是 10 秒。</span><span class="sxs-lookup"><span data-stu-id="1edbb-106">The default value for this option is 10 seconds.</span></span> <span data-ttu-id="1edbb-107">將值設定為 0 即可無限期等候。</span><span class="sxs-lookup"><span data-stu-id="1edbb-107">A value of 0 allows for an infinite wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1edbb-108">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中，這個選項的預設值是 20 秒。</span><span class="sxs-lookup"><span data-stu-id="1edbb-108">The default value for this option is 20 seconds in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="1edbb-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1edbb-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1edbb-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1edbb-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1edbb-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="1edbb-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1edbb-112">安全性</span><span class="sxs-lookup"><span data-stu-id="1edbb-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1edbb-113">**使用下列方法設定 remote login timeout 選項：**</span><span class="sxs-lookup"><span data-stu-id="1edbb-113">**To configure the remote login timeout option, using:**</span></span>  
  
     [<span data-ttu-id="1edbb-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1edbb-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1edbb-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1edbb-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="1edbb-116">**後續操作：** [設定遠端登入逾時選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1edbb-116">**Follow Up:**  [After you configure the remote login timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1edbb-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="1edbb-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1edbb-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="1edbb-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1edbb-119">**remote login timeout** 選項會影響對 OLE DB 提供者所做的異質性查詢連接。</span><span class="sxs-lookup"><span data-stu-id="1edbb-119">The **remote login timeout** option affects connections to OLE DB providers made for heterogeneous queries.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1edbb-120">Security</span><span class="sxs-lookup"><span data-stu-id="1edbb-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1edbb-121">權限</span><span class="sxs-lookup"><span data-stu-id="1edbb-121">Permissions</span></span>  
 <span data-ttu-id="1edbb-122">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="1edbb-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="1edbb-123">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="1edbb-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="1edbb-124">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="1edbb-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1edbb-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1edbb-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="1edbb-126">設定 remote login timeout 選項</span><span class="sxs-lookup"><span data-stu-id="1edbb-126">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="1edbb-127">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1edbb-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1edbb-128">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="1edbb-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="1edbb-129">在 **[網路]** 下，為 **[遠端登入逾時]** 方塊選取一個值。</span><span class="sxs-lookup"><span data-stu-id="1edbb-129">Under **Network**, select a value for the **Remote Login Timeout** box.</span></span>  
  
     <span data-ttu-id="1edbb-130">**remote login timeout** 選項可用來指定遠端登入嘗試在傳回失敗前等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="1edbb-130">Use the **remote login timeout** option to specify the number of seconds to wait before returning from a failed remote login attempt.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1edbb-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1edbb-131">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="1edbb-132">設定 remote login timeout 選項</span><span class="sxs-lookup"><span data-stu-id="1edbb-132">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="1edbb-133">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1edbb-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1edbb-134">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1edbb-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1edbb-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1edbb-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1edbb-136">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `remote login timeout` 選項的值設定為 `35` 秒。</span><span class="sxs-lookup"><span data-stu-id="1edbb-136">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote login timeout` option to `35` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="1edbb-137">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="1edbb-137">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-login-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="1edbb-138">後續操作：設定遠端登入逾時選項之後</span><span class="sxs-lookup"><span data-stu-id="1edbb-138">Follow Up: After you configure the remote login timeout option</span></span>  
 <span data-ttu-id="1edbb-139">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="1edbb-139">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edbb-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1edbb-140">See Also</span></span>  
 <span data-ttu-id="1edbb-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1edbb-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="1edbb-142">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1edbb-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="1edbb-143">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1edbb-143">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
