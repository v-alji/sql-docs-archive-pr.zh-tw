---
title: 設定 recovery interval 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 560d514ba8dd1503b59b3b59ecf404d876e24cd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592239"
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a><span data-ttu-id="93cbe-102">設定 recovery interval 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="93cbe-102">Configure the recovery interval Server Configuration Option</span></span>
  <span data-ttu-id="93cbe-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] recovery interval [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="93cbe-103">This topic describes how to configure the **recovery interval** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="93cbe-104">**recovery interval** 選項會定義資料庫的復原時間上限。</span><span class="sxs-lookup"><span data-stu-id="93cbe-104">The **recovery interval** option defines an upper limit on the time recovering a database should take.</span></span> <span data-ttu-id="93cbe-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 使用此選項的指定值，來決定 [automatic checkpoints](../../relational-databases/logs/database-checkpoints-sql-server.md) 在給定資料庫上發出自動檢查點的大約頻率。</span><span class="sxs-lookup"><span data-stu-id="93cbe-105">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the value specified for this option to determine approximately how often [automatic checkpoints](../../relational-databases/logs/database-checkpoints-sql-server.md) to issue automatic checkpoints on a given database.</span></span>  
  
 <span data-ttu-id="93cbe-106">預設復原間隔值為 0，代表允許 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 自動設定復原間隔。</span><span class="sxs-lookup"><span data-stu-id="93cbe-106">The default recovery-interval value is 0, which allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to automatically configure the recovery interval.</span></span> <span data-ttu-id="93cbe-107">一般而言，使用中的資料庫之預設復原間隔大約是一分鐘執行一次自動檢查點，而復原總時間不超過一分鐘。</span><span class="sxs-lookup"><span data-stu-id="93cbe-107">Typically, the default recovery interval results in automatic checkpoints occurring approximately once a minute for active databases and a recovery time of less than one minute.</span></span> <span data-ttu-id="93cbe-108">較高的值表示復原預計最長時間，以分鐘為單位。</span><span class="sxs-lookup"><span data-stu-id="93cbe-108">Higher values indicate the approximate maximum recovery time, in minutes.</span></span> <span data-ttu-id="93cbe-109">例如，設定復原間隔為 3 表示復原的最長時間約 3 分鐘。</span><span class="sxs-lookup"><span data-stu-id="93cbe-109">For example, setting the recovery interval to 3 indicates a maximum recovery time of approximately three minutes.</span></span>  
  
 <span data-ttu-id="93cbe-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="93cbe-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="93cbe-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="93cbe-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="93cbe-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="93cbe-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="93cbe-113">建議</span><span class="sxs-lookup"><span data-stu-id="93cbe-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="93cbe-114">安全性</span><span class="sxs-lookup"><span data-stu-id="93cbe-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="93cbe-115">**若要使用下列項目設定 recovery interval 伺服器組態選項：**</span><span class="sxs-lookup"><span data-stu-id="93cbe-115">**To Configure the recovery interval Server Configuration Option, using:**</span></span>  
  
     [<span data-ttu-id="93cbe-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="93cbe-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="93cbe-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="93cbe-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="93cbe-118">**後續操作：** [設定復原間隔項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="93cbe-118">**Follow Up:**  [After you configure the recovery interval option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="93cbe-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="93cbe-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="93cbe-120">限制事項</span><span class="sxs-lookup"><span data-stu-id="93cbe-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="93cbe-121">復原間隔只會影響使用預設目標復原時間 (0) 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="93cbe-121">The recovery interval affects only databases that use the default target recovery time (0).</span></span> <span data-ttu-id="93cbe-122">若要覆寫資料庫上的伺服器復原間隔，請在資料庫上設定非預設目標復原時間。</span><span class="sxs-lookup"><span data-stu-id="93cbe-122">To override the server recovery interval on a database, configure a non-default target recovery time on the database.</span></span> <span data-ttu-id="93cbe-123">如需詳細資訊，請參閱 [變更資料庫的目標復原時間 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="93cbe-123">For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="93cbe-124">建議</span><span class="sxs-lookup"><span data-stu-id="93cbe-124">Recommendations</span></span>  
  
-   <span data-ttu-id="93cbe-125">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="93cbe-125">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="93cbe-126">除非出現效能問題，不然通常我們會建議您將復原間隔維持在 0。</span><span class="sxs-lookup"><span data-stu-id="93cbe-126">Typically, we recommend that you keep the recovery interval at 0, unless you experience performance problems.</span></span> <span data-ttu-id="93cbe-127">如果您決定增加復原間隔設定，我們建議您逐漸少量增加此設定，並評估每次累加對於復原效能的影響。</span><span class="sxs-lookup"><span data-stu-id="93cbe-127">If you decide to increase the recovery-interval setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance.</span></span>  
  
-   <span data-ttu-id="93cbe-128">如果您使用 **sp_configure** 將 **recovery interval** 選項設為大於 60 (分鐘) 的值，請指定 RECONFIGURE WITH OVERRIDE。</span><span class="sxs-lookup"><span data-stu-id="93cbe-128">If you use **sp_configure** to change the value of the **recovery interval** option to more than 60 (minutes), specify RECONFIGURE WITH OVERRIDE.</span></span> <span data-ttu-id="93cbe-129">WITH OVERRIDE 會停用組態值的檢查 (對於無效或非建議值的值)。</span><span class="sxs-lookup"><span data-stu-id="93cbe-129">WITH OVERRIDE disables configuration value checking (for values that are not valid or are nonrecommended values).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="93cbe-130">Security</span><span class="sxs-lookup"><span data-stu-id="93cbe-130">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="93cbe-131">權限</span><span class="sxs-lookup"><span data-stu-id="93cbe-131">Permissions</span></span>  
 <span data-ttu-id="93cbe-132">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="93cbe-132">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="93cbe-133">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="93cbe-133">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="93cbe-134">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="93cbe-134">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="93cbe-135">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="93cbe-135">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="93cbe-136">**若要設定復原間隔**</span><span class="sxs-lookup"><span data-stu-id="93cbe-136">**To set the recovery interval**</span></span>  
  
1.  <span data-ttu-id="93cbe-137">在 [物件總管] 中，以滑鼠右鍵按一下伺服器執行個體，然後選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="93cbe-137">In Object Explorer, right-click server instance and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="93cbe-138">按一下 **[資料庫設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="93cbe-138">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="93cbe-139">於 **[復原間隔 (分鐘)]** 方塊的 **[復原]** 下，輸入或選取介於 0 到 32767 之間的任一數值 (以分鐘為單位)，設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時，回復每個資料庫所花費的時間上限。</span><span class="sxs-lookup"><span data-stu-id="93cbe-139">Under **Recovery**, in the **Recovery interval (minutes)** box, type or select a value from 0 through 32767 to set the maximum amount of time, in minutes, that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should spend recovering each database at startup.</span></span> <span data-ttu-id="93cbe-140">預設值是 0，指出由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動組態。</span><span class="sxs-lookup"><span data-stu-id="93cbe-140">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93cbe-141">實務上，這表示復原時間小於一分鐘，而且使用中資料庫幾乎每分鐘有一次檢查點。</span><span class="sxs-lookup"><span data-stu-id="93cbe-141">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="93cbe-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="93cbe-142">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-recovery-interval"></a><span data-ttu-id="93cbe-143">若要設定復原間隔</span><span class="sxs-lookup"><span data-stu-id="93cbe-143">To set the recovery interval</span></span>  
  
1.  <span data-ttu-id="93cbe-144">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="93cbe-144">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="93cbe-145">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="93cbe-145">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="93cbe-146">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="93cbe-146">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="93cbe-147">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `recovery interval` 選項的值設定為 `3` 分鐘。</span><span class="sxs-lookup"><span data-stu-id="93cbe-147">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `recovery interval` option to `3` minutes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="93cbe-148">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="93cbe-148">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-recovery-internal-option"></a><a name="FollowUp"></a> <span data-ttu-id="93cbe-149">後續操作：設定復原間隔選項之後</span><span class="sxs-lookup"><span data-stu-id="93cbe-149">Follow Up: After you configure the recovery internal option</span></span>  
 <span data-ttu-id="93cbe-150">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="93cbe-150">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cbe-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93cbe-151">See Also</span></span>  
 <span data-ttu-id="93cbe-152">[變更資料庫的目標復原時間 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93cbe-152">[Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md) </span></span>  
 <span data-ttu-id="93cbe-153">[資料庫檢查點 &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93cbe-153">[Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md) </span></span>  
 <span data-ttu-id="93cbe-154">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93cbe-154">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="93cbe-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="93cbe-155">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="93cbe-156">[顯示伺服器組態選項進階選項](show-advanced-options-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="93cbe-156">[show advanced options Server Configuration Option](show-advanced-options-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="93cbe-157">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93cbe-157">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
