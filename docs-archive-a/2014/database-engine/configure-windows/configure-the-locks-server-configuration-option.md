---
title: 設定 locks 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- locks option [SQL Server]
ms.assetid: b0cf0f86-7652-4574-a9fb-908e10d03973
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e45f4cc539be585966eb0beb30d4938b504c3419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708609"
---
# <a name="configure-the-locks-server-configuration-option"></a><span data-ttu-id="73a87-102">設定 locks 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="73a87-102">Configure the locks Server Configuration Option</span></span>
  <span data-ttu-id="73a87-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] locks [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="73a87-103">This topic describes how to configure the **locks** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="73a87-104">**locks** 選項會設定可用鎖定的最大數目，藉此限制 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 用於鎖定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="73a87-104">The **locks** option sets the maximum number of available locks, thereby limiting the amount of memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for them.</span></span> <span data-ttu-id="73a87-105">預設值為 0，允許 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 根據變更系統需求，動態配置與取消配置鎖定結構。</span><span class="sxs-lookup"><span data-stu-id="73a87-105">The default setting is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically, based on changing system requirements.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="73a87-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="73a87-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="73a87-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="73a87-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="73a87-108">建議</span><span class="sxs-lookup"><span data-stu-id="73a87-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="73a87-109">安全性</span><span class="sxs-lookup"><span data-stu-id="73a87-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="73a87-110">**使用下列方法設定 locks 選項：**</span><span class="sxs-lookup"><span data-stu-id="73a87-110">**To configure the locks option, using:**</span></span>  
  
     [<span data-ttu-id="73a87-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73a87-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="73a87-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="73a87-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="73a87-113">**後續操作：** [設定鎖定選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="73a87-113">**Follow Up:**  [After you configure the locks option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="73a87-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="73a87-114">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="73a87-115">建議</span><span class="sxs-lookup"><span data-stu-id="73a87-115">Recommendations</span></span>  
  
-   <span data-ttu-id="73a87-116">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="73a87-116">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="73a87-117">如果伺服器啟動時是將 **locks** 設為 0，則鎖定管理員會從 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 取得足夠的記憶體，以供 2,500 個鎖定結構的初始集區使用。</span><span class="sxs-lookup"><span data-stu-id="73a87-117">When the server is started with **locks** set to 0, the lock manager acquires sufficient memory from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for an initial pool of 2,500 lock structures.</span></span> <span data-ttu-id="73a87-118">當鎖定集區耗盡時，就會再為集區取得額外的記憶體。</span><span class="sxs-lookup"><span data-stu-id="73a87-118">As the lock pool is exhausted, additional memory is acquired for the pool.</span></span>  
  
     <span data-ttu-id="73a87-119">一般而言，如果鎖定集區所需的記憶體多於 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 記憶體集區可提供的數量，而且還有更多的電腦記憶體可用 (尚未達到 **max server memory** 臨界值) 的話， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會動態配置記憶體，以滿足鎖定要求。</span><span class="sxs-lookup"><span data-stu-id="73a87-119">Generally, if more memory is required for the lock pool than is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool, and more computer memory is available (the **max server memory** threshold has not been reached), the [!INCLUDE[ssDE](../../includes/ssde-md.md)] allocates memory dynamically to satisfy the request for locks.</span></span> <span data-ttu-id="73a87-120">然而，如果配置該記憶體會造成作業系統層級的分頁 (例如，如果另一個應用程式與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在同一部電腦上執行而且它正在使用該記憶體)，就無法再配置鎖定空間。</span><span class="sxs-lookup"><span data-stu-id="73a87-120">However, if allocating that memory would cause paging at the operating system level (for example, if another application is running on the same computer as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and using that memory), more lock space is not allocated.</span></span> <span data-ttu-id="73a87-121">動態鎖定集區所取得的記憶體不會超過 [!INCLUDE[ssDE](../../includes/ssde-md.md)]配置記憶體的 60%。</span><span class="sxs-lookup"><span data-stu-id="73a87-121">The dynamic lock pool does not acquire more than 60 percent of the memory allocated to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="73a87-122">當鎖定集區達到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體所取得之記憶體的 60%，或電腦上沒有多餘的記憶體可用時，之後的鎖定要求都會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="73a87-122">After the lock pool has reached 60 percent of the memory acquired by an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or no more memory is available on the computer, further requests for locks generate an error.</span></span>  
  
     <span data-ttu-id="73a87-123">讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 動態地使用鎖定，是建議的設定。</span><span class="sxs-lookup"><span data-stu-id="73a87-123">Allowing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use locks dynamically is the recommended configuration.</span></span> <span data-ttu-id="73a87-124">但是，您可以設定 **locks** ，並覆寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 動態配置鎖定資源的功能。</span><span class="sxs-lookup"><span data-stu-id="73a87-124">However, you can set **locks** and override the ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allocate lock resources dynamically.</span></span> <span data-ttu-id="73a87-125">當 **locks** 設為 0 以外的數值時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 所能配置的鎖定無法超過 **locks**中指定的值。</span><span class="sxs-lookup"><span data-stu-id="73a87-125">When **locks** is set to a value other than 0, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot allocate more locks than the value specified in **locks**.</span></span> <span data-ttu-id="73a87-126">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 顯示訊息表示已超過可用的鎖定個數，就應增加這個值。</span><span class="sxs-lookup"><span data-stu-id="73a87-126">Increase this value if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a message that you have exceeded the number of available locks.</span></span> <span data-ttu-id="73a87-127">因為每個鎖定都會耗用記憶體 (每個鎖定 96 個位元組)，所以增加這個值可能需要增加伺服器專用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="73a87-127">Because each lock consumes memory (96 bytes per lock), increasing this value can require increasing the amount of memory dedicated to the server.</span></span>  
  
-   <span data-ttu-id="73a87-128">**locks** 選項也會影響發生鎖定擴大的時機。</span><span class="sxs-lookup"><span data-stu-id="73a87-128">The **locks** option also affects when lock escalation occurs.</span></span> <span data-ttu-id="73a87-129">**locks** 設為 0 時，鎖定擴大會在目前的鎖定結構所用的記憶體達到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 記憶體集區的 40% 時發生。</span><span class="sxs-lookup"><span data-stu-id="73a87-129">When **locks** is set to 0, lock escalation occurs when the memory used by the current lock structures reaches 40 percent of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] memory pool.</span></span> <span data-ttu-id="73a87-130">**locks** 未設為 0 時，鎖定擴大會在鎖定個數達到 **locks**指定數值的 40% 時發生。</span><span class="sxs-lookup"><span data-stu-id="73a87-130">When **locks** is not set to 0, lock escalation occurs when the number of locks reaches 40 percent of the value specified for **locks**.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73a87-131">Security</span><span class="sxs-lookup"><span data-stu-id="73a87-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73a87-132">權限</span><span class="sxs-lookup"><span data-stu-id="73a87-132">Permissions</span></span>  
 <span data-ttu-id="73a87-133">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="73a87-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="73a87-134">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="73a87-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="73a87-135">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="73a87-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="73a87-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73a87-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="73a87-137">若要設定 locks 選項</span><span class="sxs-lookup"><span data-stu-id="73a87-137">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="73a87-138">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="73a87-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="73a87-139">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="73a87-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="73a87-140">在 **[平行處理原則]** 下，輸入所需的 **locks** 選項值。</span><span class="sxs-lookup"><span data-stu-id="73a87-140">Under **Parallelism**, type the desired value for the **locks** option.</span></span>  
  
     <span data-ttu-id="73a87-141">使用 **locks** 選項來設定可用鎖定的最大數目，從而限制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用於鎖定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="73a87-141">Use the **locks** option to set the maximum number of available locks, thereby limiting the amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for them.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="73a87-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="73a87-142">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-locks-option"></a><span data-ttu-id="73a87-143">若要設定 locks 選項</span><span class="sxs-lookup"><span data-stu-id="73a87-143">To configure the locks option</span></span>  
  
1.  <span data-ttu-id="73a87-144">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73a87-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="73a87-145">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="73a87-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="73a87-146">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="73a87-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="73a87-147">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 設定 `locks` 選項的值，將可供所有使用者使用的鎖定數目設定為 `20000`。</span><span class="sxs-lookup"><span data-stu-id="73a87-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `locks` option to set the number of locks available for all users to `20000`.</span></span>  
  
```sql  
Use AdventureWorks2012 ;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'locks', 20000;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="73a87-148">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="73a87-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-locks-option"></a><a name="FollowUp"></a> <span data-ttu-id="73a87-149">後續操作：設定鎖定選項之後</span><span class="sxs-lookup"><span data-stu-id="73a87-149">Follow Up: After you configure the locks option</span></span>  
 <span data-ttu-id="73a87-150">伺服器必須重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="73a87-150">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a87-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73a87-151">See Also</span></span>  
 <span data-ttu-id="73a87-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73a87-152">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="73a87-153">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="73a87-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="73a87-154">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73a87-154">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
