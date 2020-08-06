---
title: 設定 user options 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- global default for all users [SQL Server]
- users [SQL Server], global defaults
- user options option [SQL Server]
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7ee40d0f6de532b93ce9d8075b609c80f09df7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707858"
---
# <a name="configure-the-user-options-server-configuration-option"></a><span data-ttu-id="0a05e-102">設定 user options 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="0a05e-102">Configure the user options Server Configuration Option</span></span>
  <span data-ttu-id="0a05e-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user options [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="0a05e-103">This topic describes how to configure the **user options** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0a05e-104">**user options** 選項指定所有使用者的全域預設值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-104">The **user options** option specifies global defaults for all users.</span></span> <span data-ttu-id="0a05e-105">會為使用者工作階段的持續時間建立預設查詢處理選項的清單。</span><span class="sxs-lookup"><span data-stu-id="0a05e-105">A list of default query processing options is established for the duration of a user's work session.</span></span> <span data-ttu-id="0a05e-106">**user options** 選項允許您變更 SET 選項的預設值 (如果伺服器的預設值不適當)。</span><span class="sxs-lookup"><span data-stu-id="0a05e-106">The **user options** option allows you to change the default values of the SET options (if the server's default settings are not appropriate).</span></span>  
  
 <span data-ttu-id="0a05e-107">使用者可以使用 SET 陳述式來覆寫這些預設值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-107">A user can override these defaults by using the SET statement.</span></span> <span data-ttu-id="0a05e-108">您可以動態設定 **user options** 以供新的登入使用。</span><span class="sxs-lookup"><span data-stu-id="0a05e-108">You can configure **user options** dynamically for new logins.</span></span> <span data-ttu-id="0a05e-109">變更 **user options**的設定之後，新的登入工作階段就會使用新的設定；目前的登入工作階段則不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="0a05e-109">After you change the setting of **user options**, new login sessions use the new setting; current login sessions are not affected.</span></span>  
  
 <span data-ttu-id="0a05e-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0a05e-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0a05e-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0a05e-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0a05e-112">建議</span><span class="sxs-lookup"><span data-stu-id="0a05e-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0a05e-113">安全性</span><span class="sxs-lookup"><span data-stu-id="0a05e-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0a05e-114">**若要使用下列項目設定 user options 組態選項：**</span><span class="sxs-lookup"><span data-stu-id="0a05e-114">**To configure the user options configuration option, using:**</span></span>  
  
     [<span data-ttu-id="0a05e-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a05e-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0a05e-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a05e-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0a05e-117">**後續操作：** [設定使用者選項設定選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0a05e-117">**Follow Up:**  [After you configure the user options configuration option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0a05e-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="0a05e-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0a05e-119">建議</span><span class="sxs-lookup"><span data-stu-id="0a05e-119">Recommendations</span></span>  
  
-   <span data-ttu-id="0a05e-120">下表列出及描述 **user options**的組態值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-120">The following table lists and describes the configuration values for **user options**.</span></span> <span data-ttu-id="0a05e-121">不是所有組態值都彼此相容。</span><span class="sxs-lookup"><span data-stu-id="0a05e-121">Not all configuration values are compatible with each other.</span></span> <span data-ttu-id="0a05e-122">例如，不能同時設定 ANSI_NULL_DFLT_ON 與 ANSI_NULL_DFLT_OFF。</span><span class="sxs-lookup"><span data-stu-id="0a05e-122">For example, ANSI_NULL_DFLT_ON and ANSI_NULL_DFLT_OFF cannot be set at the same time.</span></span>  
  
    |<span data-ttu-id="0a05e-123">值</span><span class="sxs-lookup"><span data-stu-id="0a05e-123">Value</span></span>|<span data-ttu-id="0a05e-124">組態</span><span class="sxs-lookup"><span data-stu-id="0a05e-124">Configuration</span></span>|<span data-ttu-id="0a05e-125">描述</span><span class="sxs-lookup"><span data-stu-id="0a05e-125">Description</span></span>|  
    |-----------|-------------------|-----------------|  
    |<span data-ttu-id="0a05e-126">1</span><span class="sxs-lookup"><span data-stu-id="0a05e-126">1</span></span>|<span data-ttu-id="0a05e-127">DISABLE_DEF_CNST_CHK</span><span class="sxs-lookup"><span data-stu-id="0a05e-127">DISABLE_DEF_CNST_CHK</span></span>|<span data-ttu-id="0a05e-128">控制暫時的或延遲的條件約束檢查。</span><span class="sxs-lookup"><span data-stu-id="0a05e-128">Controls interim or deferred constraint checking.</span></span>|  
    |<span data-ttu-id="0a05e-129">2</span><span class="sxs-lookup"><span data-stu-id="0a05e-129">2</span></span>|<span data-ttu-id="0a05e-130">IMPLICIT_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="0a05e-130">IMPLICIT_TRANSACTIONS</span></span>|<span data-ttu-id="0a05e-131">如果是 dblib 網路程式庫連接，則控制執行陳述式時是否隱含地啟動交易。</span><span class="sxs-lookup"><span data-stu-id="0a05e-131">For dblib network library connections, controls whether a transaction is started implicitly when a statement is executed.</span></span> <span data-ttu-id="0a05e-132">IMPLICIT_TRANSACTIONS 設定在 ODBC 或 OLEDB 連接上無效。</span><span class="sxs-lookup"><span data-stu-id="0a05e-132">The IMPLICIT_TRANSACTIONS setting has no effect on ODBC or OLEDB connections.</span></span>|  
    |<span data-ttu-id="0a05e-133">4</span><span class="sxs-lookup"><span data-stu-id="0a05e-133">4</span></span>|<span data-ttu-id="0a05e-134">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="0a05e-134">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="0a05e-135">控制執行認可作業後資料指標的行為。</span><span class="sxs-lookup"><span data-stu-id="0a05e-135">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
    |<span data-ttu-id="0a05e-136">8</span><span class="sxs-lookup"><span data-stu-id="0a05e-136">8</span></span>|<span data-ttu-id="0a05e-137">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="0a05e-137">ANSI_WARNINGS</span></span>|<span data-ttu-id="0a05e-138">控制彙總警告中的截斷與 NULL。</span><span class="sxs-lookup"><span data-stu-id="0a05e-138">Controls truncation and NULL in aggregate warnings.</span></span>|  
    |<span data-ttu-id="0a05e-139">16</span><span class="sxs-lookup"><span data-stu-id="0a05e-139">16</span></span>|<span data-ttu-id="0a05e-140">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="0a05e-140">ANSI_PADDING</span></span>|<span data-ttu-id="0a05e-141">控制固定長度變數的填補。</span><span class="sxs-lookup"><span data-stu-id="0a05e-141">Controls padding of fixed-length variables.</span></span>|  
    |<span data-ttu-id="0a05e-142">32</span><span class="sxs-lookup"><span data-stu-id="0a05e-142">32</span></span>|<span data-ttu-id="0a05e-143">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="0a05e-143">ANSI_NULLS</span></span>|<span data-ttu-id="0a05e-144">控制使用相等運算子時 NULL 的處理方式。</span><span class="sxs-lookup"><span data-stu-id="0a05e-144">Controls NULL handling when using equality operators.</span></span>|  
    |<span data-ttu-id="0a05e-145">64</span><span class="sxs-lookup"><span data-stu-id="0a05e-145">64</span></span>|<span data-ttu-id="0a05e-146">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="0a05e-146">ARITHABORT</span></span>|<span data-ttu-id="0a05e-147">查詢執行過程中發生溢位或除以零的錯誤時終止查詢。</span><span class="sxs-lookup"><span data-stu-id="0a05e-147">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
    |<span data-ttu-id="0a05e-148">128</span><span class="sxs-lookup"><span data-stu-id="0a05e-148">128</span></span>|<span data-ttu-id="0a05e-149">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="0a05e-149">ARITHIGNORE</span></span>|<span data-ttu-id="0a05e-150">查詢過程中發生溢位或除以零的錯誤時傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="0a05e-150">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
    |<span data-ttu-id="0a05e-151">256</span><span class="sxs-lookup"><span data-stu-id="0a05e-151">256</span></span>|<span data-ttu-id="0a05e-152">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="0a05e-152">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="0a05e-153">評估運算式時區別單引號與雙引號。</span><span class="sxs-lookup"><span data-stu-id="0a05e-153">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
    |<span data-ttu-id="0a05e-154">512</span><span class="sxs-lookup"><span data-stu-id="0a05e-154">512</span></span>|<span data-ttu-id="0a05e-155">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="0a05e-155">NOCOUNT</span></span>|<span data-ttu-id="0a05e-156">關閉每個陳述式結束時傳回的訊息，這些訊息會說明有多少資料列受到影響。</span><span class="sxs-lookup"><span data-stu-id="0a05e-156">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
    |<span data-ttu-id="0a05e-157">1024</span><span class="sxs-lookup"><span data-stu-id="0a05e-157">1024</span></span>|<span data-ttu-id="0a05e-158">ANSI_NULL_DFLT_ON</span><span class="sxs-lookup"><span data-stu-id="0a05e-158">ANSI_NULL_DFLT_ON</span></span>|<span data-ttu-id="0a05e-159">更改工作階段的行為，使 Null 屬性與 ANSI 相容。</span><span class="sxs-lookup"><span data-stu-id="0a05e-159">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="0a05e-160">新定義的資料行若未明確定義 Null 屬性，就允許 Null。</span><span class="sxs-lookup"><span data-stu-id="0a05e-160">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
    |<span data-ttu-id="0a05e-161">2048</span><span class="sxs-lookup"><span data-stu-id="0a05e-161">2048</span></span>|<span data-ttu-id="0a05e-162">ANSI_NULL_DFLT_OFF</span><span class="sxs-lookup"><span data-stu-id="0a05e-162">ANSI_NULL_DFLT_OFF</span></span>|<span data-ttu-id="0a05e-163">更改工作階段的行為，使 Null 屬性與 ANSI 不相容。</span><span class="sxs-lookup"><span data-stu-id="0a05e-163">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="0a05e-164">新定義的資料行若未明確定義 Null 屬性，則不允許 Null。</span><span class="sxs-lookup"><span data-stu-id="0a05e-164">New columns defined without explicit nullability do not allow nulls.</span></span>|  
    |<span data-ttu-id="0a05e-165">4096</span><span class="sxs-lookup"><span data-stu-id="0a05e-165">4096</span></span>|<span data-ttu-id="0a05e-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="0a05e-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="0a05e-167">將字串與 NULL 值串連時傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="0a05e-167">Returns NULL when concatenating a NULL value with a string.</span></span>|  
    |<span data-ttu-id="0a05e-168">8192</span><span class="sxs-lookup"><span data-stu-id="0a05e-168">8192</span></span>|<span data-ttu-id="0a05e-169">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="0a05e-169">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="0a05e-170">運算式中發生失去有效位數時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a05e-170">Generates an error when a loss of precision occurs in an expression.</span></span>|  
    |<span data-ttu-id="0a05e-171">16384</span><span class="sxs-lookup"><span data-stu-id="0a05e-171">16384</span></span>|<span data-ttu-id="0a05e-172">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="0a05e-172">XACT_ABORT</span></span>|<span data-ttu-id="0a05e-173">如果 Transact- SQL 陳述式引發執行階段錯誤，就回復交易。</span><span class="sxs-lookup"><span data-stu-id="0a05e-173">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
-   <span data-ttu-id="0a05e-174">**user options** 中的位元位置與 @@OPTIONS 中的位元位置完全一樣。</span><span class="sxs-lookup"><span data-stu-id="0a05e-174">The bit positions in **user options** are identical to those in @@OPTIONS.</span></span> <span data-ttu-id="0a05e-175">每個連接都有它自己的 @@OPTIONS 函數，代表組態環境。</span><span class="sxs-lookup"><span data-stu-id="0a05e-175">Each connection has its own @@OPTIONS function, which represents the configuration environment.</span></span> <span data-ttu-id="0a05e-176">登入 \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，使用者會收到將目前 **user options** 值指派給 @@OPTIONS 的預設環境。</span><span class="sxs-lookup"><span data-stu-id="0a05e-176">When logging in to an instance of \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a user receives a default environment that assigns the current **user options** value to @@OPTIONS.</span></span> <span data-ttu-id="0a05e-177">為 **user options** 執行 SET 陳述式會影響工作階段的 @@OPTIONS 函式中的對應值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-177">Executing SET statements for **user options** affects the corresponding value in the session's @@OPTIONS function.</span></span> <span data-ttu-id="0a05e-178">在變更這個設定值後建立的連接都會接收新的值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-178">All connections created after this setting is changed receive the new value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0a05e-179">Security</span><span class="sxs-lookup"><span data-stu-id="0a05e-179">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0a05e-180">權限</span><span class="sxs-lookup"><span data-stu-id="0a05e-180">Permissions</span></span>  
 <span data-ttu-id="0a05e-181">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="0a05e-181">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="0a05e-182">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="0a05e-182">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="0a05e-183">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="0a05e-183">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0a05e-184">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0a05e-184">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="0a05e-185">若要設定 user options 組態選項</span><span class="sxs-lookup"><span data-stu-id="0a05e-185">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="0a05e-186">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0a05e-186">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0a05e-187">按一下 **[連接]** 節點。</span><span class="sxs-lookup"><span data-stu-id="0a05e-187">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="0a05e-188">在 **[預設連接選項]** 方塊中，選取一個或多個屬性來設定所有連接的使用者的預設查詢處理選項。</span><span class="sxs-lookup"><span data-stu-id="0a05e-188">In the **Default connection options** box, select one or more attributes to configure the default query-processing options for all connected users.</span></span>  
  
     <span data-ttu-id="0a05e-189">預設是無設定任何使用者選項。</span><span class="sxs-lookup"><span data-stu-id="0a05e-189">By default, no user options are configured.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0a05e-190">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0a05e-190">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="0a05e-191">若要設定 user options 組態選項</span><span class="sxs-lookup"><span data-stu-id="0a05e-191">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="0a05e-192">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a05e-192">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0a05e-193">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0a05e-193">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0a05e-194">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0a05e-194">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0a05e-195">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 設定 `user options` ，以變更 ANSI_WARNINGS 伺服器選項的設定值。</span><span class="sxs-lookup"><span data-stu-id="0a05e-195">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `user options` to change the setting for the ANSI_WARNINGS server option.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-user-options-configuration-option"></a><a name="FollowUp"></a> <span data-ttu-id="0a05e-196">後續操作：設定使用者選項設定選項之後</span><span class="sxs-lookup"><span data-stu-id="0a05e-196">Follow Up: After you configure the user options configuration option</span></span>  
 <span data-ttu-id="0a05e-197">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a05e-197">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a05e-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a05e-198">See Also</span></span>  
 <span data-ttu-id="0a05e-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a05e-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0a05e-200">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a05e-200">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="0a05e-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a05e-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="0a05e-202">SET 陳述式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0a05e-202">SET Statements &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statements-transact-sql)  
  
  
