---
title: 設定 min memory per query 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 56d85f36840f0900c8b5e986334a99ba610d3930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597339"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a><span data-ttu-id="f24f2-102">設定 min memory per query 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="f24f2-102">Configure the min memory per query Server Configuration Option</span></span>
  <span data-ttu-id="f24f2-103">本主題描述如何 `min memory per query` 使用或，在中設定 server configuration 選項 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f24f2-103">This topic describes how to configure the `min memory per query` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f24f2-104">`min memory per query`選項會指定將為執行查詢而配置的最小記憶體數量) （以 kb 為單位） (。</span><span class="sxs-lookup"><span data-stu-id="f24f2-104">The `min memory per query` option specifies the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span> <span data-ttu-id="f24f2-105">例如，如果 `min memory per query` 設定為 2048 KB，則查詢保證至少會取得記憶體總計。</span><span class="sxs-lookup"><span data-stu-id="f24f2-105">For example, if `min memory per query` is set to 2,048 KB, the query is guaranteed to get at least that much total memory.</span></span> <span data-ttu-id="f24f2-106">預設值為 1,024 KB。</span><span class="sxs-lookup"><span data-stu-id="f24f2-106">The default value is 1,024 KB.</span></span> <span data-ttu-id="f24f2-107">最小值是 512 KB，最大值則是 2,147,483,647 KB (2 GB)。</span><span class="sxs-lookup"><span data-stu-id="f24f2-107">The minimum value 512 KB, and the maximum is 2,147,483,647 KB (2 GB).</span></span>  
  
 <span data-ttu-id="f24f2-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f24f2-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f24f2-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f24f2-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f24f2-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="f24f2-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f24f2-111">建議</span><span class="sxs-lookup"><span data-stu-id="f24f2-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f24f2-112">安全性</span><span class="sxs-lookup"><span data-stu-id="f24f2-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f24f2-113">**使用下列方法設定 min memory per query 選項：**</span><span class="sxs-lookup"><span data-stu-id="f24f2-113">**To configure the min memory per query option, using:**</span></span>  
  
     [<span data-ttu-id="f24f2-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f24f2-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f24f2-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f24f2-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f24f2-116">**後續操作：** [設定每個查詢的最小記憶體選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f24f2-116">**Follow Up:**  [After you configure the min memory per query option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f24f2-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="f24f2-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f24f2-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="f24f2-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f24f2-119">[每個查詢的最小記憶體] 的優先順序高於 [[索引建立記憶體] 選項](configure-the-index-create-memory-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="f24f2-119">The amount of min memory per query has precedence over the [index create memory Option](configure-the-index-create-memory-server-configuration-option.md).</span></span> <span data-ttu-id="f24f2-120">若您同時變更了兩個選項，且索引建立記憶體選項小於每個查詢的最小記憶體，您會看到警告訊息，但仍會設定該值。</span><span class="sxs-lookup"><span data-stu-id="f24f2-120">If you modify both options and the index create memory is less than min memory per query, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="f24f2-121">執行查詢時，您會看到另一個類似的警告。</span><span class="sxs-lookup"><span data-stu-id="f24f2-121">During query execution you receive another similar warning.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f24f2-122">建議</span><span class="sxs-lookup"><span data-stu-id="f24f2-122">Recommendations</span></span>  
  
-   <span data-ttu-id="f24f2-123">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="f24f2-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="f24f2-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢處理器會嘗試判斷要配置給查詢的最佳記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="f24f2-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query processor tries to determine the optimal amount of memory to allocate to a query.</span></span> <span data-ttu-id="f24f2-125">min memory per query 選項可讓系統管理員指定任何單一查詢所接收的最小記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="f24f2-125">The min memory per query option lets the administrator specify the minimum amount of memory any single query receives.</span></span> <span data-ttu-id="f24f2-126">若查詢中含有大量資料的雜湊和排序作業，則這些查詢通常會接收比此值更多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f24f2-126">Queries generally receive more memory than this if they have hash and sort operations on a large volume of data.</span></span> <span data-ttu-id="f24f2-127">提高 min memory per query 的值也許可以改善一些小型至中型查詢的效能，但這樣做也可能導致競用記憶體資源的情形增加。</span><span class="sxs-lookup"><span data-stu-id="f24f2-127">Increasing the value of min memory per query may improve performance for some small to medium-sized queries, but doing so could lead to increased competition for memory resources.</span></span> <span data-ttu-id="f24f2-128">每個查詢的最小記憶體選項包含了為進行排序所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f24f2-128">The min memory per query option includes memory allocated for sorting.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f24f2-129">Security</span><span class="sxs-lookup"><span data-stu-id="f24f2-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f24f2-130">權限</span><span class="sxs-lookup"><span data-stu-id="f24f2-130">Permissions</span></span>  
 <span data-ttu-id="f24f2-131">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="f24f2-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="f24f2-132">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="f24f2-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="f24f2-133">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="f24f2-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f24f2-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f24f2-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="f24f2-135">設定 min memory per query 選項</span><span class="sxs-lookup"><span data-stu-id="f24f2-135">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="f24f2-136">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f24f2-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f24f2-137">按一下 **[記憶體]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f24f2-137">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="f24f2-138">在 **[每個查詢的最小記憶體]** 方塊中，輸入將為執行查詢而配置的最小記憶體數量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="f24f2-138">In the **Minimum memory per query** box, enter the minimum amount of memory (in kilobytes) that will be allocated for the execution of a query.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f24f2-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f24f2-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a><span data-ttu-id="f24f2-140">設定 min memory per query 選項</span><span class="sxs-lookup"><span data-stu-id="f24f2-140">To configure the min memory per query option</span></span>  
  
1.  <span data-ttu-id="f24f2-141">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f24f2-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f24f2-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f24f2-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f24f2-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f24f2-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f24f2-144">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `min memory per query` 選項的值設定為 `3500` KB。</span><span class="sxs-lookup"><span data-stu-id="f24f2-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `min memory per query` option to `3500` KB.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a> <span data-ttu-id="f24f2-145">後續操作：設定每個查詢的最小記憶體選項之後</span><span class="sxs-lookup"><span data-stu-id="f24f2-145">Follow Up: After you configure the min memory per query option</span></span>  
 <span data-ttu-id="f24f2-146">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="f24f2-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24f2-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f24f2-147">See Also</span></span>  
 <span data-ttu-id="f24f2-148">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f24f2-148">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f24f2-149">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f24f2-149">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="f24f2-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f24f2-150">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="f24f2-151">設定 index create memory 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="f24f2-151">Configure the index create memory Server Configuration Option</span></span>](configure-the-index-create-memory-server-configuration-option.md)  
  
  
