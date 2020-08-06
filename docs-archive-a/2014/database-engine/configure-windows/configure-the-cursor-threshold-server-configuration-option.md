---
title: 設定 cursor threshold 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d7fd9ecafda270a02f1fba9f5dd74adc9e299d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607092"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a><span data-ttu-id="a8776-102">設定 cursor threshold 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="a8776-102">Configure the cursor threshold Server Configuration Option</span></span>
  <span data-ttu-id="a8776-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cursor threshold [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a8776-103">This topic describes how to configure the **cursor threshold** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a8776-104">**cursor threshold** 選項會指定資料指標集中以非同步方式產生資料指標索引鍵集的列數。</span><span class="sxs-lookup"><span data-stu-id="a8776-104">The **cursor threshold** option specifies the number of rows in the cursor set at which cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="a8776-105">當資料指標為結果集產生索引鍵集時，查詢最佳化工具會估計將在該結果集傳回的資料列數。</span><span class="sxs-lookup"><span data-stu-id="a8776-105">When cursors generate a keyset for a result set, the query optimizer estimates the number of rows that will be returned for that result set.</span></span> <span data-ttu-id="a8776-106">如果查詢最佳化工具估計將傳回的列數會大於這個臨界值，就會以非同步方式產生資料指標，讓使用者在資料指標繼續擴展的同時，可以從資料指標擷取資料列。</span><span class="sxs-lookup"><span data-stu-id="a8776-106">If the query optimizer estimates that the number of returned rows is greater than this threshold, the cursor is generated asynchronously, allowing the user to fetch rows from the cursor while the cursor continues to be populated.</span></span> <span data-ttu-id="a8776-107">否則，會以同步的方式產生資料指標，使查詢等到所有資料列都傳回為止。</span><span class="sxs-lookup"><span data-stu-id="a8776-107">Otherwise, the cursor is generated synchronously, and the query waits until all rows are returned.</span></span>  
  
 <span data-ttu-id="a8776-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a8776-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a8776-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a8776-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a8776-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="a8776-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a8776-111">建議</span><span class="sxs-lookup"><span data-stu-id="a8776-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a8776-112">安全性</span><span class="sxs-lookup"><span data-stu-id="a8776-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a8776-113">**使用下列方法設定 cursor threshold 選項：**</span><span class="sxs-lookup"><span data-stu-id="a8776-113">**To configure the cursor threshold option, using:**</span></span>  
  
     [<span data-ttu-id="a8776-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8776-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a8776-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8776-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a8776-116">**後續操作：** [設定資料指標閾值選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a8776-116">**Follow Up:**  [After you configure the cursor threshold option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a8776-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="a8776-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a8776-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="a8776-118">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8776-119">不支援非同步產生索引鍵集驅動或靜態 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料指標。</span><span class="sxs-lookup"><span data-stu-id="a8776-119">does not support generating keyset-driven or static [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors asynchronously.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a8776-120">資料指標作業是以批次方式來處理，因此，不需要非同步產生 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料指標。</span><span class="sxs-lookup"><span data-stu-id="a8776-120">cursor operations such as OPEN or FETCH are batched, so there is no need for the asynchronous generation of [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8776-121">會繼續支援非同步索引鍵集驅動或靜態應用程式開發介面 (API) 伺服器資料指標，其中低度延遲 OPEN 會是一個顧慮，因為每一個資料指標作業都需要用戶端往返。</span><span class="sxs-lookup"><span data-stu-id="a8776-121">continues to support asynchronous keyset-driven or static application programming interface (API) server cursors where low latency OPEN is a concern, due to client round trips for each cursor operation.</span></span>  
  
-   <span data-ttu-id="a8776-122">查詢最佳化工具用來決定索引鍵集中估計資料列數的精確度，須視資料指標中每個資料表統計資料的準確度而定。</span><span class="sxs-lookup"><span data-stu-id="a8776-122">The accuracy of the query optimizer to determine an estimate for the number of rows in a keyset depends on the currency of the statistics for each of the tables in the cursor.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a8776-123">建議</span><span class="sxs-lookup"><span data-stu-id="a8776-123">Recommendations</span></span>  
  
-   <span data-ttu-id="a8776-124">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="a8776-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="a8776-125">如果將 [資料指標臨界值] 設定為 -1，所有索引鍵集都會以同步方式產生，這有益於小型的資料指標集。</span><span class="sxs-lookup"><span data-stu-id="a8776-125">If you set **cursor threshold** to -1, all keysets are generated synchronously, which benefits small cursor sets.</span></span> <span data-ttu-id="a8776-126">如果將 **cursor threshold** 設成 0，所有資料指標索引鍵集都會以非同步方式產生。</span><span class="sxs-lookup"><span data-stu-id="a8776-126">If you set **cursor threshold** to 0, all cursor keysets are generated asynchronously.</span></span> <span data-ttu-id="a8776-127">若使用其他值，查詢最佳化工具會比較資料指標集中預期的列數，如果列數超過 **cursor threshold**中設定的數字，就以非同步方式建立索引鍵集。</span><span class="sxs-lookup"><span data-stu-id="a8776-127">With other values, the query optimizer compares the number of expected rows in the cursor set and builds the keyset asynchronously if it exceeds the number set in **cursor threshold**.</span></span> <span data-ttu-id="a8776-128">請不要將 **cursor threshold** 設得太低，因為小的結果集最好是以同步的方式建立。</span><span class="sxs-lookup"><span data-stu-id="a8776-128">Do not set **cursor threshold** too low, because small result sets are better built synchronously.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a8776-129">Security</span><span class="sxs-lookup"><span data-stu-id="a8776-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a8776-130">權限</span><span class="sxs-lookup"><span data-stu-id="a8776-130">Permissions</span></span>  
 <span data-ttu-id="a8776-131">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="a8776-131">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a8776-132">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="a8776-132">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a8776-133">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="a8776-133">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a8776-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8776-134">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="a8776-135">若要設定資料指標臨界值選項</span><span class="sxs-lookup"><span data-stu-id="a8776-135">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="a8776-136">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a8776-136">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a8776-137">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a8776-137">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="a8776-138">在 **[其他]** 下，將 **[資料指標臨界值]** 選項變更為所要的值。</span><span class="sxs-lookup"><span data-stu-id="a8776-138">Under **Miscellaneous**, change the **Cursor Threshold** option to the value you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a8776-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8776-139">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cursor-threshold-option"></a><span data-ttu-id="a8776-140">若要設定資料指標臨界值選項</span><span class="sxs-lookup"><span data-stu-id="a8776-140">To configure the cursor threshold option</span></span>  
  
1.  <span data-ttu-id="a8776-141">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8776-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a8776-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a8776-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a8776-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a8776-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a8776-144">這個範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `cursor threshold` 選項設定為 `0` ，以便以非同步方式產生資料指標索引鍵集。</span><span class="sxs-lookup"><span data-stu-id="a8776-144">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the `cursor threshold` option to `0` so that cursor keysets are generated asynchronously.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="a8776-145">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a8776-145">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cursor-threshold-option"></a><a name="FollowUp"></a> <span data-ttu-id="a8776-146">後續操作：設定資料指標閾值選項之後</span><span class="sxs-lookup"><span data-stu-id="a8776-146">Follow Up: After you configure the cursor threshold option</span></span>  
 <span data-ttu-id="a8776-147">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8776-147">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8776-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8776-148">See Also</span></span>  
 <span data-ttu-id="a8776-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8776-149">[@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql) </span></span>  
 <span data-ttu-id="a8776-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8776-150">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a8776-151">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8776-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="a8776-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8776-152">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="a8776-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8776-153">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
