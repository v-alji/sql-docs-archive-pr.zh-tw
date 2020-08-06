---
title: 設定 index create memory 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd0aeb93d3fb68089338335068fdaaae19919fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700216"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a><span data-ttu-id="99df0-102">設定 index create memory 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="99df0-102">Configure the index create memory Server Configuration Option</span></span>
  <span data-ttu-id="99df0-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] index create memory [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="99df0-103">This topic describes how to configure the **index create memory** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="99df0-104">**index create memory** 選項會控制最初配置來建立索引的記憶體數量上限。</span><span class="sxs-lookup"><span data-stu-id="99df0-104">The **index create memory** option controls the maximum amount of memory initially allocated for creating indexes.</span></span> <span data-ttu-id="99df0-105">這個選項的預設值是 0 (自我設定)。</span><span class="sxs-lookup"><span data-stu-id="99df0-105">The default value for this option is 0 (self-configuring).</span></span> <span data-ttu-id="99df0-106">若稍後在建立索引時需要更多記憶體，且有足夠的記憶體可用，則伺服器會使用該記憶體，因而超過此選項的設定。</span><span class="sxs-lookup"><span data-stu-id="99df0-106">If more memory is later needed for index creation and the memory is available, the server will use it; thereby, exceeding the setting of this option.</span></span> <span data-ttu-id="99df0-107">若沒有更多可用的記憶體，則會使用預先配置的記憶體繼續進行索引建立作業。</span><span class="sxs-lookup"><span data-stu-id="99df0-107">If additional memory is not available, the index creation will continue using the memory already allocated.</span></span>  
  
 <span data-ttu-id="99df0-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="99df0-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="99df0-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="99df0-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99df0-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="99df0-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="99df0-111">建議</span><span class="sxs-lookup"><span data-stu-id="99df0-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="99df0-112">安全性</span><span class="sxs-lookup"><span data-stu-id="99df0-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="99df0-113">**使用下列方法設定 index create memory 選項：**</span><span class="sxs-lookup"><span data-stu-id="99df0-113">**To configure the index create memory option, using:**</span></span>  
  
     [<span data-ttu-id="99df0-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99df0-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="99df0-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99df0-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="99df0-116">**後續操作：** [設定索引建立記憶體選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="99df0-116">**Follow Up:**  [After you configure the index create memory option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99df0-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="99df0-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="99df0-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="99df0-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="99df0-119">**[每個查詢的最小記憶體]** 選項之設定，優先順序高於 **[索引建立記憶體]** 選項。</span><span class="sxs-lookup"><span data-stu-id="99df0-119">The setting of the **min memory per query** option has precedence over the **index create memory** option.</span></span> <span data-ttu-id="99df0-120">若您同時變更了兩個選項，且 **index create memory** 小於 **min memory per query**，您會看到警告訊息，但仍會設定該值。</span><span class="sxs-lookup"><span data-stu-id="99df0-120">If you change both options and the **index create memory** is less than **min memory per query**, you receive a warning message, but the value is set.</span></span> <span data-ttu-id="99df0-121">執行查詢時，您會看到同樣的警告。</span><span class="sxs-lookup"><span data-stu-id="99df0-121">During query execution, you receive a similar warning.</span></span>  
  
-   <span data-ttu-id="99df0-122">使用資料分割資料表與索引時，如果有非對齊之資料分割索引與高度平行處理，建立索引時所需的最低記憶體需求會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="99df0-122">When using partitioned tables and indexes, the minimum memory requirements for index creation may increase significantly if there are non-aligned partitioned indexes and a high degree of parallelism.</span></span> <span data-ttu-id="99df0-123">此選項會控制在單一索引建立作業中，為所有索引資料分割配置的初始記憶體數量總計。</span><span class="sxs-lookup"><span data-stu-id="99df0-123">This option controls the total initial amount of memory allocated for all index partitions in a single index creation operation.</span></span> <span data-ttu-id="99df0-124">若此選項設定的記憶體數量小於執行查詢所需的最低記憶體需求，則查詢會終止，且會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="99df0-124">The query will terminate with an error message if the amount set by this option is less than the minimum required to run the query.</span></span>  
  
-   <span data-ttu-id="99df0-125">此選項的執行值將不會超過執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之作業系統與硬體平台可用的實際記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="99df0-125">The run value for this option will not exceed the actual amount of memory that can be used for the operating system and hardware platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="99df0-126">在 32 位元作業系統上，執行值會低於 3 GB。</span><span class="sxs-lookup"><span data-stu-id="99df0-126">On 32-bit operating systems, the run value will be less than 3 gigabytes (GB).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="99df0-127">建議</span><span class="sxs-lookup"><span data-stu-id="99df0-127">Recommendations</span></span>  
  
-   <span data-ttu-id="99df0-128">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="99df0-128">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="99df0-129">**[索引建立記憶體]** 選項為自我設定，並且通常不需要調整便可使用。</span><span class="sxs-lookup"><span data-stu-id="99df0-129">The **index create memory** option is self-configuring and usually works without requiring adjustment.</span></span> <span data-ttu-id="99df0-130">然而，如果無法建立索引，請考慮增加這個選項的執行值。</span><span class="sxs-lookup"><span data-stu-id="99df0-130">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99df0-131">Security</span><span class="sxs-lookup"><span data-stu-id="99df0-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99df0-132">權限</span><span class="sxs-lookup"><span data-stu-id="99df0-132">Permissions</span></span>  
 <span data-ttu-id="99df0-133">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="99df0-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="99df0-134">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="99df0-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="99df0-135">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="99df0-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99df0-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99df0-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="99df0-137">若要設定 index create memory 選項</span><span class="sxs-lookup"><span data-stu-id="99df0-137">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="99df0-138">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="99df0-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="99df0-139">按一下 **[記憶體]** 節點。</span><span class="sxs-lookup"><span data-stu-id="99df0-139">Click the **Memory** node.</span></span>  
  
3.  <span data-ttu-id="99df0-140">在 **[索引建立記憶體]** 之下，輸入或選取所要的索引建立記憶體選項值。</span><span class="sxs-lookup"><span data-stu-id="99df0-140">Under **Index creation memory**, type or select the desired value for the index create memory option.</span></span>  
  
     <span data-ttu-id="99df0-141">**index create memory** 選項可用來控制索引建立排序所使用的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="99df0-141">Use the **index create memory** option to control the amount of memory used by index creation sorts.</span></span> <span data-ttu-id="99df0-142">[索引建立記憶體] 屬於自我設定的選項，而且不需調整即可適用於大部份情況。</span><span class="sxs-lookup"><span data-stu-id="99df0-142">The **index create memory** option is self-configuring and should work in most cases without requiring adjustment.</span></span> <span data-ttu-id="99df0-143">然而，如果無法建立索引，請考慮增加這個選項的執行值。</span><span class="sxs-lookup"><span data-stu-id="99df0-143">However, if you experience difficulties creating indexes, consider increasing the value of this option from its run value.</span></span> <span data-ttu-id="99df0-144">查詢排序是透過 **min memory per query** 選項來控制。</span><span class="sxs-lookup"><span data-stu-id="99df0-144">Query sorts are controlled through the **min memory per query** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99df0-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99df0-145">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-index-create-memory-option"></a><span data-ttu-id="99df0-146">若要設定 index create memory 選項</span><span class="sxs-lookup"><span data-stu-id="99df0-146">To configure the index create memory option</span></span>  
  
1.  <span data-ttu-id="99df0-147">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99df0-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="99df0-148">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="99df0-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="99df0-149">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="99df0-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="99df0-150">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `index create memory` 選項的值設定為 `4096`。</span><span class="sxs-lookup"><span data-stu-id="99df0-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `index create memory` option to `4096`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="99df0-151">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="99df0-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a> <span data-ttu-id="99df0-152">後續操作：設定索引建立記憶體選項之後</span><span class="sxs-lookup"><span data-stu-id="99df0-152">Follow Up: After you configure the index create memory option</span></span>  
 <span data-ttu-id="99df0-153">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="99df0-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99df0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99df0-154">See Also</span></span>  
 <span data-ttu-id="99df0-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="99df0-155">[sys.configurations &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) </span></span>  
 <span data-ttu-id="99df0-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="99df0-156">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="99df0-157">[伺服器記憶體伺服器組態選項](server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="99df0-157">[Server Memory Server Configuration Options](server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="99df0-158">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99df0-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="99df0-159">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99df0-159">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
