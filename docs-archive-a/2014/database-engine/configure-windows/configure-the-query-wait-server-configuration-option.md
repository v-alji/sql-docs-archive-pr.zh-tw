---
title: 設定 query wait 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], timing out
- time [SQL Server], query wait time
- query wait option [SQL Server]
ms.assetid: 0fc4aa01-65a3-4a33-9ef4-caca41add238
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 638afff2aa05a9fc4e61bc71e8610dba1dda8cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597336"
---
# <a name="configure-the-query-wait-server-configuration-option"></a><span data-ttu-id="f6d39-102">設定 query wait 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="f6d39-102">Configure the query wait Server Configuration Option</span></span>
  <span data-ttu-id="f6d39-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] query wait [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="f6d39-103">This topic describes how to configure the **query wait** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f6d39-104">如果因為記憶體不足，無法執行會使用大量記憶體的查詢 (例如涉及排序與雜湊的查詢)，則這些查詢會排入佇列中。</span><span class="sxs-lookup"><span data-stu-id="f6d39-104">Memory-intensive queries (such as those involving sorting and hashing) are queued when there is not enough memory available to run the query.</span></span> <span data-ttu-id="f6d39-105">**query wait** 選項會指定逾時前，查詢等候資源的秒數 (從 0 到 2147483647)。這個選項的預設值是 -1。</span><span class="sxs-lookup"><span data-stu-id="f6d39-105">The **query wait** option specifies the time, in seconds (from 0 through 2147483647), that a query waits for resources before it times out. The default value for this option is -1.</span></span> <span data-ttu-id="f6d39-106">這表示逾時時間就會是估計查詢成本的 25 倍。</span><span class="sxs-lookup"><span data-stu-id="f6d39-106">This means the time-out is calculated as 25 times the estimated query cost.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6d39-107">當查詢在等候記憶體時，包含等候中查詢的交易可能會持有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f6d39-107">A transaction that contains the waiting query might hold locks while the query waits for memory.</span></span> <span data-ttu-id="f6d39-108">在極少數的情況下，可能會發生無法偵測的死結。</span><span class="sxs-lookup"><span data-stu-id="f6d39-108">In rare situations, it is possible for an undetectable deadlock to occur.</span></span> <span data-ttu-id="f6d39-109">減少查詢等候時間會降低發生這類死結的可能性。</span><span class="sxs-lookup"><span data-stu-id="f6d39-109">Decreasing the query wait time lowers the probability of such deadlocks.</span></span> <span data-ttu-id="f6d39-110">最後，等待的查詢會終止，並釋放其交易鎖定。</span><span class="sxs-lookup"><span data-stu-id="f6d39-110">Eventually, a waiting query will be terminated and the transaction locks released.</span></span> <span data-ttu-id="f6d39-111">然而增加等候時間的上限，可能會增加終止前的查詢時間量。</span><span class="sxs-lookup"><span data-stu-id="f6d39-111">However, increasing the maximum wait time may increase the amount of time for the query to be terminated.</span></span> <span data-ttu-id="f6d39-112">不建議您更改這個選項。</span><span class="sxs-lookup"><span data-stu-id="f6d39-112">Changes to this option are not recommended.</span></span>  
  
 <span data-ttu-id="f6d39-113">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f6d39-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6d39-114">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f6d39-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6d39-115">建議</span><span class="sxs-lookup"><span data-stu-id="f6d39-115">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f6d39-116">安全性</span><span class="sxs-lookup"><span data-stu-id="f6d39-116">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6d39-117">**若要使用下列項目設定 query wait 選項：**</span><span class="sxs-lookup"><span data-stu-id="f6d39-117">**To configure the query wait option, using:**</span></span>  
  
     [<span data-ttu-id="f6d39-118">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6d39-118">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6d39-119">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6d39-119">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f6d39-120">**後續操作：** [設定查詢等候選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f6d39-120">**Follow Up:**  [After you configure the query wait option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6d39-121">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6d39-121">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f6d39-122">建議</span><span class="sxs-lookup"><span data-stu-id="f6d39-122">Recommendations</span></span>  
  
-   <span data-ttu-id="f6d39-123">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="f6d39-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6d39-124">Security</span><span class="sxs-lookup"><span data-stu-id="f6d39-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6d39-125">權限</span><span class="sxs-lookup"><span data-stu-id="f6d39-125">Permissions</span></span>  
 <span data-ttu-id="f6d39-126">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="f6d39-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="f6d39-127">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="f6d39-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="f6d39-128">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="f6d39-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6d39-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6d39-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="f6d39-130">若要設定查詢等候選項</span><span class="sxs-lookup"><span data-stu-id="f6d39-130">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="f6d39-131">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f6d39-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f6d39-132">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f6d39-132">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="f6d39-133">在 **[平行處理原則]** 下方，為 **query wait** 選項輸入想要的值。</span><span class="sxs-lookup"><span data-stu-id="f6d39-133">Under **Parallelism**, type the desired value for the **query wait** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6d39-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6d39-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-query-wait-option"></a><span data-ttu-id="f6d39-135">若要設定查詢等候選項</span><span class="sxs-lookup"><span data-stu-id="f6d39-135">To configure the query wait option</span></span>  
  
1.  <span data-ttu-id="f6d39-136">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6d39-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6d39-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f6d39-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6d39-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f6d39-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f6d39-139">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `query wait` 選項的值設定為 `7500` 秒。</span><span class="sxs-lookup"><span data-stu-id="f6d39-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `query wait` option to `7500` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query wait', 7500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="f6d39-140">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="f6d39-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-query-wait-option"></a><a name="FollowUp"></a> <span data-ttu-id="f6d39-141">後續操作：設定查詢等候選項之後</span><span class="sxs-lookup"><span data-stu-id="f6d39-141">Follow Up: After you configure the query wait option</span></span>  
 <span data-ttu-id="f6d39-142">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6d39-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d39-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d39-143">See Also</span></span>  
 <span data-ttu-id="f6d39-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6d39-144">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f6d39-145">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6d39-145">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="f6d39-146">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6d39-146">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
