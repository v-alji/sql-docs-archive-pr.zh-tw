---
title: 設定 default full-text language 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585591"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a><span data-ttu-id="0a720-102">設定 default full-text language 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="0a720-102">Configure the default full-text language Server Configuration Option</span></span>
  <span data-ttu-id="0a720-103">本主題描述如何 `default full-text language` 使用或，在中設定 server configuration 選項 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0a720-103">This topic describes how to configure the `default full-text language` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0a720-104">`default full-text language`選項會指定全文檢索索引的預設語言值。</span><span class="sxs-lookup"><span data-stu-id="0a720-104">The `default full-text language` option specifies a default language value for full-text indexes.</span></span> <span data-ttu-id="0a720-105">語言分析會針對已全文檢索索引的所有資料執行，而且相依於資料的語言。</span><span class="sxs-lookup"><span data-stu-id="0a720-105">Linguistic analysis is performed on all data that is full-text indexed and is dependent on the language of the data.</span></span> <span data-ttu-id="0a720-106">這個選項的預設值是伺服器使用的語言。</span><span class="sxs-lookup"><span data-stu-id="0a720-106">The default value of this option is the language of the server.</span></span> <span data-ttu-id="0a720-107">若為當地語系化的版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會將 `default full-text language` 選項設定為伺服器的語言（如果有適當的相符項存在的話）。</span><span class="sxs-lookup"><span data-stu-id="0a720-107">For a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup sets the `default full-text language` option to the language of the server if an appropriate match exists.</span></span> <span data-ttu-id="0a720-108">若 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 為非當地語系化的版本時，則 `default full-text language` 選項會是英文。</span><span class="sxs-lookup"><span data-stu-id="0a720-108">For a non-localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the `default full-text language` option is English.</span></span>  
  
 <span data-ttu-id="0a720-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0a720-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0a720-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0a720-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0a720-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="0a720-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0a720-112">建議</span><span class="sxs-lookup"><span data-stu-id="0a720-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0a720-113">安全性</span><span class="sxs-lookup"><span data-stu-id="0a720-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0a720-114">**使用下列方法設定 default full-text language 選項：**</span><span class="sxs-lookup"><span data-stu-id="0a720-114">**To configure the default full-text language option, using:**</span></span>  
  
     [<span data-ttu-id="0a720-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a720-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0a720-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a720-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0a720-117">**後續操作：** [設定預設全文檢索語言選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0a720-117">**Follow Up:**  [After you configure the default full-text language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0a720-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="0a720-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0a720-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="0a720-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0a720-120">`default full-text language`當未透過 CREATE 全文檢索索引或 ALTER 全文檢索索引語句中的 language **language_term**選項指定資料行的語言時，會在全文檢索索引中使用選項的值。</span><span class="sxs-lookup"><span data-stu-id="0a720-120">The value of the `default full-text language` option is used in a full-text index when no language is specified for a column through the LANGUAGE **language_term** option in the CREATE FULLTEXT INDEX or ALTER FULLTEXT INDEX statements.</span></span> <span data-ttu-id="0a720-121">如果不支援預設的全文檢索語言或無法使用語言分析封裝 (Linguistic Analysis Package)，CREATE 或 ALTER 作業會失敗，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將傳回錯誤訊息，表示指定的語言無效。</span><span class="sxs-lookup"><span data-stu-id="0a720-121">If the default full-text language is not supported or the linguistic analysis package is not available, the CREATE or ALTER operation will fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will return an error message stating that the language specified is not valid.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0a720-122">建議</span><span class="sxs-lookup"><span data-stu-id="0a720-122">Recommendations</span></span>  
  
-   <span data-ttu-id="0a720-123">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="0a720-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="0a720-124">`default full-text language`選項需要 LCID 值。</span><span class="sxs-lookup"><span data-stu-id="0a720-124">The `default full-text language` option requires an LCID value.</span></span> <span data-ttu-id="0a720-125">如需受支援的 LCID 及其相關語言的清單，請參閱 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0a720-125">For a list of supported LCIDs and their related languages, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span> <span data-ttu-id="0a720-126">例如，其他語言也可以向獨立軟體廠商取得。</span><span class="sxs-lookup"><span data-stu-id="0a720-126">Other languages may also be available from independent software vendors, for example.</span></span> <span data-ttu-id="0a720-127">如果找不到特定的語言方言，全文檢索引擎就會自動切換至主要語言。</span><span class="sxs-lookup"><span data-stu-id="0a720-127">If no specific language dialect is found, the Full-Text Engine will automatically switch to the primary language.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0a720-128">Security</span><span class="sxs-lookup"><span data-stu-id="0a720-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0a720-129">權限</span><span class="sxs-lookup"><span data-stu-id="0a720-129">Permissions</span></span>  
 <span data-ttu-id="0a720-130">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="0a720-130">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="0a720-131">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="0a720-131">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="0a720-132">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="0a720-132">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0a720-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a720-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="0a720-134">設定 default full-text language 選項</span><span class="sxs-lookup"><span data-stu-id="0a720-134">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="0a720-135">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0a720-135">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0a720-136">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="0a720-136">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="0a720-137">在 [其他] 下方，使用 **[預設全文檢索語言]** 來指定全文檢索索引資料行的預設語言值。</span><span class="sxs-lookup"><span data-stu-id="0a720-137">Under Miscellaneous, use **Default Full Text Language** to specify a default language value for full-text indexed columns.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0a720-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a720-138">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="0a720-139">設定 default full-text language 選項</span><span class="sxs-lookup"><span data-stu-id="0a720-139">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="0a720-140">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a720-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0a720-141">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0a720-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0a720-142">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0a720-142">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0a720-143">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `default full-text` 選項的值設定為荷蘭文 (`1043`)。</span><span class="sxs-lookup"><span data-stu-id="0a720-143">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `default full-text` option to Dutch (`1043`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="0a720-144">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="0a720-144">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="0a720-145">後續操作：設定預設全文檢索語言選項之後</span><span class="sxs-lookup"><span data-stu-id="0a720-145">Follow Up: After you configure the default full-text language option</span></span>  
 <span data-ttu-id="0a720-146">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a720-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a720-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a720-147">See Also</span></span>  
 <span data-ttu-id="0a720-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a720-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span></span>  
 <span data-ttu-id="0a720-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a720-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0a720-150">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a720-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="0a720-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a720-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="0a720-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a720-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="0a720-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0a720-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
