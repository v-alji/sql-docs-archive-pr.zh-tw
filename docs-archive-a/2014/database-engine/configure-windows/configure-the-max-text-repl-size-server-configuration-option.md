---
title: 設定 max text repl size 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af0cf426583ee328f0a484de1c3539836c0d8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597344"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a><span data-ttu-id="cd1e4-102">設定 max text repl size 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="cd1e4-102">Configure the max text repl size Server Configuration Option</span></span>
  <span data-ttu-id="cd1e4-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max text repl size [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-103">This topic describes how to configure the **max text repl size** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cd1e4-104">[**最大文字複寫大小**] 選項會指定在 `text` `ntext` `varchar(max)` `nvarchar(max)` `varbinary(max)` `xml` `image` 單一 INSERT、UPDATE、WRITETEXT 或 UPDATETEXT 語句中，可以加入至複寫資料行或已捕捉資料行的、、、、、和資料的大小上限 (（以位元組為單位) ）。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-104">The **max text repl size** option specifies the maximum size (in bytes) of `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, `xml`, and `image` data that can be added to a replicated column or captured column in a single INSERT, UPDATE, WRITETEXT, or UPDATETEXT statement.</span></span> <span data-ttu-id="cd1e4-105">預設值為 65536 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-105">The default value is 65536 bytes.</span></span> <span data-ttu-id="cd1e4-106">值為 -1 表示沒有任何大小限制 (除了資料類型所加諸的限制以外)。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-106">A value of -1 indicates that there is no size limit, other than the limit imposed by the data type.</span></span>  
  
 <span data-ttu-id="cd1e4-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cd1e4-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cd1e4-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cd1e4-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cd1e4-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="cd1e4-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cd1e4-110">安全性</span><span class="sxs-lookup"><span data-stu-id="cd1e4-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cd1e4-111">**使用下列方法設定 max text repl size 選項：**</span><span class="sxs-lookup"><span data-stu-id="cd1e4-111">**To configure the max text repl size option, using:**</span></span>  
  
     [<span data-ttu-id="cd1e4-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cd1e4-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cd1e4-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cd1e4-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="cd1e4-114">**後續操作：** [設定 max text repl size 選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cd1e4-114">**Follow Up:**  [After you configure the max text repl size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cd1e4-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd1e4-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cd1e4-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="cd1e4-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cd1e4-117">這個選項適用於異動複寫和異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-117">This option applies to transactional replication and Change Data Capture.</span></span> <span data-ttu-id="cd1e4-118">當同時針對異動複寫和異動資料擷取設定伺服器時，指定的值會套用到這兩個功能。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-118">When a server is configured for both transactional replication and Change Data Capture, the specified value applies to both features.</span></span> <span data-ttu-id="cd1e4-119">快照式複寫與合併式複寫會忽略這個選項。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-119">This option is ignored by snapshot replication and merge replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cd1e4-120">Security</span><span class="sxs-lookup"><span data-stu-id="cd1e4-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cd1e4-121">權限</span><span class="sxs-lookup"><span data-stu-id="cd1e4-121">Permissions</span></span>  
 <span data-ttu-id="cd1e4-122">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="cd1e4-123">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="cd1e4-124">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cd1e4-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cd1e4-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="cd1e4-126">若要設定 max text repl size 選項</span><span class="sxs-lookup"><span data-stu-id="cd1e4-126">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="cd1e4-127">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="cd1e4-128">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="cd1e4-129">在 **[其他]** 下，將 **[文字複寫大小上限]** 選項變更為所要的值。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-129">Under **Miscellaneous**, change the **Max Text Replication Size** option to the desired value.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cd1e4-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cd1e4-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a><span data-ttu-id="cd1e4-131">若要設定 max text repl size 選項</span><span class="sxs-lookup"><span data-stu-id="cd1e4-131">To configure the max text repl size option</span></span>  
  
1.  <span data-ttu-id="cd1e4-132">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cd1e4-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cd1e4-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cd1e4-135">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `max text repl size` 選項設定為 `-1`。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-135">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max text repl size` option to `-1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 <span data-ttu-id="cd1e4-136">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-136">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-text-repl-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="cd1e4-137">後續操作：設定 max text repl size 選項之後</span><span class="sxs-lookup"><span data-stu-id="cd1e4-137">Follow Up: After you configure the max text repl size option</span></span>  
 <span data-ttu-id="cd1e4-138">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd1e4-138">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1e4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1e4-139">See Also</span></span>  
 <span data-ttu-id="cd1e4-140">[SQL Server 複寫](../../relational-databases/replication/sql-server-replication.md) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-140">[SQL Server Replication](../../relational-databases/replication/sql-server-replication.md) </span></span>  
 <span data-ttu-id="cd1e4-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-141">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="cd1e4-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="cd1e4-143">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="cd1e4-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-144">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="cd1e4-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-145">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 <span data-ttu-id="cd1e4-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd1e4-146">[UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql) </span></span>  
 [<span data-ttu-id="cd1e4-147">WRITETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd1e4-147">WRITETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/writetext-transact-sql)  
  
  
