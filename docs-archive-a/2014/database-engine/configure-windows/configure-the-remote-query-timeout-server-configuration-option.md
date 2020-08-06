---
title: 設定 remote query timeout 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 74f82d621d7f0375a6a3ca604abba00f83fc6024
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707862"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a><span data-ttu-id="9bc5c-102">設定 remote query timeout 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="9bc5c-102">Configure the remote query timeout Server Configuration Option</span></span>
  <span data-ttu-id="9bc5c-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote query timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-103">This topic describes how to configure the **remote query timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9bc5c-104">**remote query timeout** 選項會指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 逾時之前，遠端作業可以執行多久 (以秒為單位)。此選項的預設值是 600，這允許 10 分鐘的等待。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-104">The **remote query timeout** option specifies how long, in seconds, a remote operation can take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default value for this option is 600, which allows a 10-minute wait.</span></span> <span data-ttu-id="9bc5c-105">此值可套用到由 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 啟始做為遠端查詢的傳出連接。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-105">This value applies to an outgoing connection initiated by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] as a remote query.</span></span> <span data-ttu-id="9bc5c-106">此值對 [!INCLUDE[ssDE](../../includes/ssde-md.md)]收到的查詢沒有影響。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-106">This value has no effect on queries received by the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="9bc5c-107">若要停用逾時，請將值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-107">To disable the time-out, set the value to 0.</span></span> <span data-ttu-id="9bc5c-108">查詢會等候，直到完成。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-108">A query will wait until it completes.</span></span>  
  
 <span data-ttu-id="9bc5c-109">對於異質性查詢，[遠端查詢逾時] 可指定遠端提供者在等候查詢結果集時，應等候幾秒 (使用 DBPROP_COMMANDTIMEOUT 資料列集屬性在命令物件中初始化) 後，查詢才會逾時。這個值也用來設定 DBPROP_GENERALTIMEOUT (如果遠端提供者支援的話)。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-109">For heterogeneous queries, **remote query timeout** specifies the number of seconds (initialized in the command object using the DBPROP_COMMANDTIMEOUT rowset property) that a remote provider should wait for result sets before the query times out. This value is also used to set DBPROP_GENERALTIMEOUT if supported by the remote provider.</span></span> <span data-ttu-id="9bc5c-110">這會使其他任何作業在指定秒數後變逾時。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-110">This will cause any other operations to time out after the specified number of seconds.</span></span>  
  
 <span data-ttu-id="9bc5c-111">對於遠端預存程序， **remote query timeout** 會指定在傳送遠端 `EXEC` 陳述式之後，遠端預存程序逾時之前必須經過的秒數。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-111">For remote stored procedures, **remote query timeout** specifies the number of seconds that must elapse after sending a remote `EXEC` statement before the remote stored procedure times out.</span></span>  
  
 <span data-ttu-id="9bc5c-112">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9bc5c-112">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9bc5c-113">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9bc5c-113">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9bc5c-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="9bc5c-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="9bc5c-115">安全性</span><span class="sxs-lookup"><span data-stu-id="9bc5c-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9bc5c-116">**使用下列方法設定 remote query timeout 選項：**</span><span class="sxs-lookup"><span data-stu-id="9bc5c-116">**To configure the remote query timeout option, using:**</span></span>  
  
     [<span data-ttu-id="9bc5c-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9bc5c-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9bc5c-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9bc5c-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="9bc5c-119">**後續操作：** [設定遠端查詢逾時選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9bc5c-119">**Follow Up:**  [After you configure the remote query timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9bc5c-120">開始之前</span><span class="sxs-lookup"><span data-stu-id="9bc5c-120">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9bc5c-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="9bc5c-121">Prerequisites</span></span>  
  
-   <span data-ttu-id="9bc5c-122">設定這個數值之前必須先允許遠端伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-122">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9bc5c-123">Security</span><span class="sxs-lookup"><span data-stu-id="9bc5c-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9bc5c-124">權限</span><span class="sxs-lookup"><span data-stu-id="9bc5c-124">Permissions</span></span>  
 <span data-ttu-id="9bc5c-125">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-125">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="9bc5c-126">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-126">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="9bc5c-127">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9bc5c-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9bc5c-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="9bc5c-129">設定 remote query timeout 選項</span><span class="sxs-lookup"><span data-stu-id="9bc5c-129">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="9bc5c-130">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-130">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9bc5c-131">按一下 **[連接]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-131">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="9bc5c-132">請在 **[遠端伺服器連接]** 下方的 **[遠端查詢逾時]** 方塊中，輸入或選取從 0 至 2,147,483,647 的值，以設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在逾時之前要等待的最大秒數。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-132">Under **Remote server connections**, in the **Remote query timeout** box, type or select a value from 0 through 2,147,483,647 to set the maximum number seconds for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to wait before timing out.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9bc5c-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9bc5c-133">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a><span data-ttu-id="9bc5c-134">設定 remote query timeout 選項</span><span class="sxs-lookup"><span data-stu-id="9bc5c-134">To configure the remote query timeout option</span></span>  
  
1.  <span data-ttu-id="9bc5c-135">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9bc5c-136">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9bc5c-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9bc5c-138">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `remote query timeout` 選項的值設定為 `0` ，以停用逾時。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-138">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote query timeout` option to `0` to disable the time-out.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="9bc5c-139">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-139">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-query-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="9bc5c-140">後續操作：設定遠端查詢逾時選項之後</span><span class="sxs-lookup"><span data-stu-id="9bc5c-140">Follow Up: After you configure the remote query timeout option</span></span>  
 <span data-ttu-id="9bc5c-141">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="9bc5c-141">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc5c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bc5c-142">See Also</span></span>  
 <span data-ttu-id="9bc5c-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9bc5c-143">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="9bc5c-144">[資料列集屬性和行為](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="9bc5c-144">[Rowset Properties and Behaviors](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 <span data-ttu-id="9bc5c-145">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bc5c-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="9bc5c-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bc5c-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
