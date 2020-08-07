---
title: 從記錄傳送設定中移除次要資料庫 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 119f2762d41d0787b6b3279507e9671e89fddfca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597318"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="947de-102">從記錄傳送組態中移除次要資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="947de-102">Remove a Secondary Database from a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="947de-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 移除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的記錄傳送次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="947de-103">This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="947de-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="947de-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="947de-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="947de-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="947de-106">安全性</span><span class="sxs-lookup"><span data-stu-id="947de-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="947de-107">**若要移除記錄傳送次要資料庫，請使用：**</span><span class="sxs-lookup"><span data-stu-id="947de-107">**To remove a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="947de-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="947de-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="947de-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="947de-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="947de-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="947de-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="947de-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="947de-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="947de-112">Security</span><span class="sxs-lookup"><span data-stu-id="947de-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="947de-113">權限</span><span class="sxs-lookup"><span data-stu-id="947de-113">Permissions</span></span>  
 <span data-ttu-id="947de-114">記錄傳送預存程序需要 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="947de-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="947de-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="947de-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a><span data-ttu-id="947de-116">若要移除記錄傳送次要資料庫</span><span class="sxs-lookup"><span data-stu-id="947de-116">To remove a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="947de-117">連接至目前是記錄傳送主要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="947de-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="947de-118">展開 [資料庫]，以滑鼠右鍵按一下記錄傳送主要資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="947de-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="947de-119">在 **[選取頁面]** 下，按一下 **[交易記錄傳送]** 。</span><span class="sxs-lookup"><span data-stu-id="947de-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="947de-120">在 **[次要伺服器執行個體與資料庫]** 下，按一下您要移除的資料庫。</span><span class="sxs-lookup"><span data-stu-id="947de-120">Under **Secondary server instances and databases**, click the database you want to remove.</span></span>  
  
5.  <span data-ttu-id="947de-121">按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="947de-121">Click **Remove**.</span></span>  
  
6.  <span data-ttu-id="947de-122">按一下 **[確定]** 以更新組態。</span><span class="sxs-lookup"><span data-stu-id="947de-122">Click **OK** to update the configuration.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="947de-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="947de-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-secondary-database"></a><span data-ttu-id="947de-124">若要移除次要資料庫</span><span class="sxs-lookup"><span data-stu-id="947de-124">To Remove a Secondary Database</span></span>  
  
1.  <span data-ttu-id="947de-125">在主要伺服器上，執行 [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) 以刪除主要伺服器上關於次要資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="947de-125">On the primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="947de-126">在次要伺服器上，執行 [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) 以刪除次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="947de-126">On the secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="947de-127">如果沒有具有相同次要識別碼的其他次要資料庫，就會從 **sp_delete_log_shipping_secondary_database** 叫用 **sp_delete_log_shipping_secondary_primary** ，並刪除次要識別碼的項目與複製及還原作業。</span><span class="sxs-lookup"><span data-stu-id="947de-127">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="947de-128">在次要伺服器上停用複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="947de-128">On the secondary server, disable the copy and restore jobs.</span></span> <span data-ttu-id="947de-129">如需詳細資訊，請參閱 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="947de-129">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="947de-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="947de-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="947de-131">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-131">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="947de-132">設定記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-132">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="947de-133">將次要資料庫加入至記錄傳送組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-133">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="947de-134">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-134">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="947de-135">檢視記錄傳送報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-135">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="947de-136">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-136">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="947de-137">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="947de-137">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="947de-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="947de-138">See Also</span></span>  
 <span data-ttu-id="947de-139">[關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="947de-139">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="947de-140">記錄傳送資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="947de-140">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
