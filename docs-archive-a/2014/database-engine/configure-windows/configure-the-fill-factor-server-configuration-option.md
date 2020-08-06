---
title: 設定 fill factor 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fill factor option [SQL Server]
ms.assetid: b920ec34-ba8b-4bb8-af53-a3ffd06bafa6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02258c92b4a09277d371e605fd4729ba9fda3461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596905"
---
# <a name="configure-the-fill-factor-server-configuration-option"></a><span data-ttu-id="c4004-102">設定 fill factor 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="c4004-102">Configure the fill factor Server Configuration Option</span></span>
  <span data-ttu-id="c4004-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fill factor [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="c4004-103">This topic describes how to configure the **fill factor** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c4004-104">提供填滿因數的用意，是為了微調索引資料的儲存與效能。</span><span class="sxs-lookup"><span data-stu-id="c4004-104">Fill factor is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="c4004-105">建立或重建索引時，填滿因數值會決定要在每個分葉層級頁面上填滿資料的空間百分比，進而保留剩餘百分比當做可用空間，以供未來成長使用。</span><span class="sxs-lookup"><span data-stu-id="c4004-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the rest as free space for future growth.</span></span> <span data-ttu-id="c4004-106">如需詳細資訊，請參閱 [指定索引的填滿因素](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="c4004-106">For more information, see [Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
 <span data-ttu-id="c4004-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c4004-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c4004-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c4004-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c4004-109">建議</span><span class="sxs-lookup"><span data-stu-id="c4004-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c4004-110">安全性</span><span class="sxs-lookup"><span data-stu-id="c4004-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c4004-111">**使用下列方法設定 fill factor 選項：**</span><span class="sxs-lookup"><span data-stu-id="c4004-111">**To configure the fill factor option, using:**</span></span>  
  
     [<span data-ttu-id="c4004-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4004-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c4004-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4004-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c4004-114">**後續操作：** [設定填滿因數選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c4004-114">**Follow Up:**  [After you configure the fill factor option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4004-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="c4004-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c4004-116">建議</span><span class="sxs-lookup"><span data-stu-id="c4004-116">Recommendations</span></span>  
  
-   <span data-ttu-id="c4004-117">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="c4004-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c4004-118">Security</span><span class="sxs-lookup"><span data-stu-id="c4004-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4004-119">權限</span><span class="sxs-lookup"><span data-stu-id="c4004-119">Permissions</span></span>  
 <span data-ttu-id="c4004-120">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="c4004-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="c4004-121">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="c4004-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="c4004-122">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="c4004-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4004-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4004-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="c4004-124">設定 fill factor 選項</span><span class="sxs-lookup"><span data-stu-id="c4004-124">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="c4004-125">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="c4004-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c4004-126">按一下 **[資料庫設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="c4004-126">Click the **Database Settings** node.</span></span>  
  
3.  <span data-ttu-id="c4004-127">在 **[預設索引填滿因數]** 方塊中，輸入或選取所要的索引填滿因數。</span><span class="sxs-lookup"><span data-stu-id="c4004-127">In the **Default index fill factor** box, type or select the index fill factor that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4004-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4004-128">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="c4004-129">設定 fill factor 選項</span><span class="sxs-lookup"><span data-stu-id="c4004-129">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="c4004-130">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4004-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c4004-131">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c4004-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c4004-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c4004-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c4004-133">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `fill factor` 選項的值設定為 `100`。</span><span class="sxs-lookup"><span data-stu-id="c4004-133">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `fill factor` option to `100`.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="c4004-134">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="c4004-134">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-fill-factor-option"></a><a name="FollowUp"></a> <span data-ttu-id="c4004-135">後續操作：設定填滿因數選項之後</span><span class="sxs-lookup"><span data-stu-id="c4004-135">Follow Up: After you configure the fill factor option</span></span>  
 <span data-ttu-id="c4004-136">伺服器必須重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="c4004-136">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4004-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4004-137">See Also</span></span>  
 <span data-ttu-id="c4004-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4004-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c4004-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4004-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="c4004-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4004-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="c4004-141">[指定索引的填滿因素](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="c4004-141">[Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span></span>  
 <span data-ttu-id="c4004-142">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4004-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c4004-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4004-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c4004-144">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c4004-144">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
