---
title: 設定 query governor cost limit 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4f8420bf8ed8c08d3626c797968c041a40f7c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592240"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a><span data-ttu-id="cde13-102">設定 query governor cost limit 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="cde13-102">Configure the query governor cost limit Server Configuration Option</span></span>
  <span data-ttu-id="cde13-103">本主題描述如何 `query governor cost limit` 使用或，在中設定 server configuration 選項 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cde13-103">This topic describes how to configure the `query governor cost limit` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cde13-104">查詢管理員成本限制選項指定查詢可執行的時間週期上限。</span><span class="sxs-lookup"><span data-stu-id="cde13-104">The query governor cost limit option specifies an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="cde13-105">查詢成本代表在特定的硬體組態上，預估完成查詢所需的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="cde13-105">Query cost refers to the estimated elapsed time, in seconds, that is required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="cde13-106">此選項的預設值為 0，這會將查詢管理員設定為關閉。</span><span class="sxs-lookup"><span data-stu-id="cde13-106">The default value for this option is 0, which sets the query governor to off.</span></span> <span data-ttu-id="cde13-107">這允許所有查詢在沒有任何時間限制下執行。</span><span class="sxs-lookup"><span data-stu-id="cde13-107">This allows all queries to run without any time limitation.</span></span> <span data-ttu-id="cde13-108">如果指定非零的非負值，查詢若超過該值的估計成本，查詢管理員就不允許執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="cde13-108">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost that exceeds that value.</span></span>  
  
 <span data-ttu-id="cde13-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cde13-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cde13-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cde13-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cde13-111">建議</span><span class="sxs-lookup"><span data-stu-id="cde13-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="cde13-112">安全性</span><span class="sxs-lookup"><span data-stu-id="cde13-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cde13-113">**使用下列方法設定 query governor cost limit 選項：**</span><span class="sxs-lookup"><span data-stu-id="cde13-113">**To configure the query governor cost limit option, using:**</span></span>  
  
     [<span data-ttu-id="cde13-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cde13-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cde13-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cde13-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="cde13-116">**後續操作：** [設定查詢管理員成本限制選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cde13-116">**Follow Up:**  [After you configure the query governor cost limit option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cde13-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="cde13-117">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cde13-118">建議</span><span class="sxs-lookup"><span data-stu-id="cde13-118">Recommendations</span></span>  
  
-   <span data-ttu-id="cde13-119">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="cde13-119">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="cde13-120">若要根據每個連接變更 query governor cost limit 值，請使用 [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cde13-120">To change the value query governor cost limit on a per-connection basis, use the [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cde13-121">Security</span><span class="sxs-lookup"><span data-stu-id="cde13-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cde13-122">權限</span><span class="sxs-lookup"><span data-stu-id="cde13-122">Permissions</span></span>  
 <span data-ttu-id="cde13-123">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="cde13-123">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="cde13-124">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="cde13-124">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="cde13-125">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="cde13-125">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cde13-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cde13-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="cde13-127">設定 query governor cost limit 選項</span><span class="sxs-lookup"><span data-stu-id="cde13-127">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="cde13-128">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="cde13-128">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="cde13-129">按一下 **[連接]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="cde13-129">Click the **Connections** page.</span></span>  
  
3.  <span data-ttu-id="cde13-130">選取或清除 **[使用查詢管理員防止執行時間很長的查詢]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cde13-130">Select or clear the **Use query governor to prevent long-running queries** check box.</span></span>  
  
     <span data-ttu-id="cde13-131">如果您選取此核取方塊，請在下方方塊中輸入一個正值，這是查詢管理員用來禁止執行任何長度超過該值的查詢。</span><span class="sxs-lookup"><span data-stu-id="cde13-131">If you select this check box, in the box below, enter a positive value, which the query governor uses to disallow execution of any query with a running length exceeding that value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cde13-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cde13-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a><span data-ttu-id="cde13-133">設定 query governor cost limit 選項</span><span class="sxs-lookup"><span data-stu-id="cde13-133">To configure the query governor cost limit option</span></span>  
  
1.  <span data-ttu-id="cde13-134">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cde13-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cde13-135">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cde13-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cde13-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cde13-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cde13-137">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `query governor cost limit` 選項的值設定為 `120` 秒。</span><span class="sxs-lookup"><span data-stu-id="cde13-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query governor cost limit` option to `120` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="cde13-138">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="cde13-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-governor-cost-limit-option"></a><a name="FollowUp"></a> <span data-ttu-id="cde13-139">後續操作：設定查詢管理員成本限制選項之後</span><span class="sxs-lookup"><span data-stu-id="cde13-139">Follow Up: After you configure the query governor cost limit option</span></span>  
 <span data-ttu-id="cde13-140">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="cde13-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde13-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cde13-141">See Also</span></span>  
 <span data-ttu-id="cde13-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cde13-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="cde13-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cde13-143">[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) </span></span>  
 <span data-ttu-id="cde13-144">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cde13-144">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="cde13-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cde13-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
