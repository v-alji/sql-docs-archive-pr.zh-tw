---
title: 移除記錄傳送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], removing
- removing log shipping
- deleting log shipping
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14fdc36c66073e89dcc2014aed4319a2ce78a98f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596249"
---
# <a name="remove-log-shipping-sql-server"></a><span data-ttu-id="926dc-102">移除記錄傳送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="926dc-102">Remove Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="926dc-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 移除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="926dc-103">This topic describes how to remove log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="926dc-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="926dc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="926dc-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="926dc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="926dc-106">安全性</span><span class="sxs-lookup"><span data-stu-id="926dc-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="926dc-107">**若要移除記錄傳送，請使用：**</span><span class="sxs-lookup"><span data-stu-id="926dc-107">**To remove log shipping, using:**</span></span>  
  
     [<span data-ttu-id="926dc-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="926dc-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="926dc-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="926dc-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="926dc-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="926dc-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="926dc-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="926dc-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="926dc-112">Security</span><span class="sxs-lookup"><span data-stu-id="926dc-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="926dc-113">權限</span><span class="sxs-lookup"><span data-stu-id="926dc-113">Permissions</span></span>  
 <span data-ttu-id="926dc-114">記錄傳送預存程序需要 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="926dc-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="926dc-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="926dc-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="926dc-116">若要移除記錄傳送</span><span class="sxs-lookup"><span data-stu-id="926dc-116">To remove log shipping</span></span>  
  
1.  <span data-ttu-id="926dc-117">連接至目前是記錄傳送主要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="926dc-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="926dc-118">展開 [資料庫]，以滑鼠右鍵按一下記錄傳送主要資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="926dc-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="926dc-119">在 **[選取頁面]** 下，按一下 **[交易記錄傳送]** 。</span><span class="sxs-lookup"><span data-stu-id="926dc-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="926dc-120">清除 **[將此啟用為記錄傳送組態的主要資料庫 ]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="926dc-120">Clear the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
5.  <span data-ttu-id="926dc-121">按一下 **[確定]** ，以便從這個主要資料庫移除記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="926dc-121">Click **OK** to remove log shipping from this primary database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="926dc-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="926dc-122">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="926dc-123">若要移除記錄傳送</span><span class="sxs-lookup"><span data-stu-id="926dc-123">To Remove Log Shipping</span></span>  
  
1.  <span data-ttu-id="926dc-124">在記錄傳送主要伺服器上執行 [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) ，以刪除主要伺服器上的次要資料庫相關資訊。</span><span class="sxs-lookup"><span data-stu-id="926dc-124">On the log shipping primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="926dc-125">在記錄傳送次要伺服器上執行 [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) ，以刪除次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="926dc-125">On the log shipping secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="926dc-126">如果沒有具有相同次要識別碼的其他次要資料庫，就會從 **sp_delete_log_shipping_secondary_database** 叫用 **sp_delete_log_shipping_secondary_primary** ，並刪除次要識別碼的項目與複製及還原作業。</span><span class="sxs-lookup"><span data-stu-id="926dc-126">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="926dc-127">在記錄傳送主要伺服器上執行 **sp_delete_log_shipping_primary_database** ，以刪除主要伺服器上的記錄傳送設定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="926dc-127">On the log shipping primary server, execute **sp_delete_log_shipping_primary_database** to delete information about the log shipping configuration from the primary server.</span></span> <span data-ttu-id="926dc-128">這也會刪除備份作業。</span><span class="sxs-lookup"><span data-stu-id="926dc-128">This also deletes the backup job.</span></span>  
  
4.  <span data-ttu-id="926dc-129">在記錄傳送主要伺服器上，停用備份作業。</span><span class="sxs-lookup"><span data-stu-id="926dc-129">On the log shipping primary server, disable the backup job.</span></span> <span data-ttu-id="926dc-130">如需詳細資訊，請參閱 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="926dc-130">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
5.  <span data-ttu-id="926dc-131">在記錄傳送次要伺服器上，停用複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="926dc-131">On the log shipping secondary server, disable the copy and restore jobs.</span></span>  
  
6.  <span data-ttu-id="926dc-132">若您不再需要使用記錄傳送次要資料庫，也可選擇從次要伺服器中刪除該資料庫。</span><span class="sxs-lookup"><span data-stu-id="926dc-132">Optionally, if you are no longer using the log shipping secondary database, you can delete it from the secondary server.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="926dc-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="926dc-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="926dc-134">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-134">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="926dc-135">設定記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-135">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="926dc-136">將次要資料庫加入至記錄傳送組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-136">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="926dc-137">從記錄傳送組態中移除次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-137">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="926dc-138">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-138">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="926dc-139">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="926dc-139">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="926dc-140">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="926dc-140">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
## <a name="see-also"></a><span data-ttu-id="926dc-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="926dc-141">See Also</span></span>  
 <span data-ttu-id="926dc-142">[關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="926dc-142">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="926dc-143">記錄傳送資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="926dc-143">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
