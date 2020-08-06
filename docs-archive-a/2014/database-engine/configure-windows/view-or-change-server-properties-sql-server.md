---
title: 檢視或變更伺服器屬性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 415d4e2d1aaa3166ae4df2dea53b34e064544e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688193"
---
# <a name="view-or-change-server-properties-sql-server"></a><span data-ttu-id="63e1f-102">檢視或變更伺服器屬性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63e1f-102">View or Change Server Properties (SQL Server)</span></span>
  <span data-ttu-id="63e1f-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 組態管理員檢視或變更 [!INCLUDE[tsql](../../includes/tsql-md.md)]執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="63e1f-103">This topic describes how to view or change the properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Configuration Manager.</span></span>  
  
 <span data-ttu-id="63e1f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="63e1f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63e1f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="63e1f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63e1f-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="63e1f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="63e1f-107">安全性</span><span class="sxs-lookup"><span data-stu-id="63e1f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="63e1f-108">**若要檢視或變更伺服器屬性，使用：**</span><span class="sxs-lookup"><span data-stu-id="63e1f-108">**To view or change server properties, using:**</span></span>  
  
     [<span data-ttu-id="63e1f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63e1f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="63e1f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63e1f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="63e1f-111">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="63e1f-111">SQL Server Configuration Manager</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="63e1f-112">**後續操作：**  [變更伺服器屬性之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="63e1f-112">**Follow Up:**  [After you change server properties](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63e1f-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="63e1f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="63e1f-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="63e1f-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="63e1f-115">使用 sp_configure 時，您必須在設定組態選項之後，執行 RECONFIGURE 或 RECONFIGURE WITH OVERRIDE。</span><span class="sxs-lookup"><span data-stu-id="63e1f-115">When using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option.</span></span> <span data-ttu-id="63e1f-116">RECONFIGURE WITH OVERRIDE 陳述式通常是保留給應該非常小心使用的組態選項。</span><span class="sxs-lookup"><span data-stu-id="63e1f-116">The RECONFIGURE WITH OVERRIDE statement is usually reserved for configuration options that should be used with extreme caution.</span></span> <span data-ttu-id="63e1f-117">但是 RECONFIGURE WITH OVERRIDE 對所有組態選項都有效，所以它可以取代 RECONFIGURE。</span><span class="sxs-lookup"><span data-stu-id="63e1f-117">However, RECONFIGURE WITH OVERRIDE works for all configuration options, and you can use it in place of RECONFIGURE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63e1f-118">RECONFIGURE 會在交易中執行。</span><span class="sxs-lookup"><span data-stu-id="63e1f-118">RECONFIGURE executes within a transaction.</span></span> <span data-ttu-id="63e1f-119">如果任何重新設定作業失敗，所有重新設定作業都不會生效。</span><span class="sxs-lookup"><span data-stu-id="63e1f-119">If any of the reconfigure operations fail, none of the reconfigure operations will take effect.</span></span>  
  
-   <span data-ttu-id="63e1f-120">有些屬性頁面會透過 Windows Management Instrumentation (WMI) 取得資訊。</span><span class="sxs-lookup"><span data-stu-id="63e1f-120">Some property pages present information obtained via Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="63e1f-121">若要顯示這些頁面，您必須將 WMI 安裝在執行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的電腦上。</span><span class="sxs-lookup"><span data-stu-id="63e1f-121">To display those pages, WMI must be installed on the computer running [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63e1f-122">Security</span><span class="sxs-lookup"><span data-stu-id="63e1f-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63e1f-123">權限</span><span class="sxs-lookup"><span data-stu-id="63e1f-123">Permissions</span></span>  
 <span data-ttu-id="63e1f-124">如需詳細資訊，請參閱 [伺服器層級角色](../../relational-databases/security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="63e1f-124">For more information, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>  
  
 <span data-ttu-id="63e1f-125">`sp_configure`預設會將不含參數或只含第一個參數的執行許可權授與給所有使用者。</span><span class="sxs-lookup"><span data-stu-id="63e1f-125">Execute permissions on `sp_configure` with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="63e1f-126">若要 `sp_configure` 使用這兩個參數來執行，以變更設定選項，或執行重新設定語句，必須將 ALTER SETTINGS 伺服器層級許可權授與使用者。</span><span class="sxs-lookup"><span data-stu-id="63e1f-126">To execute `sp_configure` with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="63e1f-127">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="63e1f-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63e1f-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63e1f-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="63e1f-129">檢視或變更伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-129">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="63e1f-130">在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-130">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="63e1f-131">在 **[伺服器屬性]** 對話方塊中，按一下頁面以檢視或變更有關該頁面的伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="63e1f-131">In the **Server Properties** dialog box, click a page to view or change server information about that page.</span></span> <span data-ttu-id="63e1f-132">部分屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="63e1f-132">Some properties are read-only.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="63e1f-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63e1f-133">Using Transact-SQL</span></span>  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a><span data-ttu-id="63e1f-134">若要使用 SERVERPROPERTY 內建函數檢視伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-134">To view server properties by using the SERVERPROPERTY built-in function</span></span>  
  
1.  <span data-ttu-id="63e1f-135">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63e1f-136">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63e1f-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63e1f-138">這個範例會在 [陳述式中使用](/sql/t-sql/functions/serverproperty-transact-sql) SERVERPROPERTY `SELECT` 內建函數傳回目前伺服器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63e1f-138">This example uses the [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) built-in function in a `SELECT` statement to return information about the current server.</span></span> <span data-ttu-id="63e1f-139">當 Windows 伺服器安裝了多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，且用戶端必須開啟另一項連接來連到目前連接所用的相同執行個體時，這個狀況非常有用。</span><span class="sxs-lookup"><span data-stu-id="63e1f-139">This scenario is useful when there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on a Windows-based server, and the client must open another connection to the same instance that is used by the current connection.</span></span>  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a><span data-ttu-id="63e1f-140">若要使用 sys.servers 類別目錄檢視表檢視伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-140">To view server properties by using the sys.servers catalog view</span></span>  
  
1.  <span data-ttu-id="63e1f-141">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63e1f-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63e1f-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63e1f-144">這個範例會查詢 [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) 目錄檢視，以傳回目前伺服器的名稱 (`name`) 和識別碼 (`server_id`)，以及用來連接到連結之伺服器的 OLE DB 提供者名稱 (`provider`)。</span><span class="sxs-lookup"><span data-stu-id="63e1f-144">This example queries the [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) catalog view to return the name (`name`) and ID (`server_id`) of the current server, and the name of the OLE DB provider (`provider`) for connecting to a linked server.</span></span>  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a><span data-ttu-id="63e1f-145">若要使用 sys.configurations 類別目錄檢視表檢視伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-145">To view server properties by using the sys.configurations catalog view</span></span>  
  
1.  <span data-ttu-id="63e1f-146">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63e1f-147">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63e1f-148">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-148">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63e1f-149">這個範例會查詢 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 類別目錄檢視，以傳回目前伺服器上每個伺服器組態選項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63e1f-149">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to return information about each server configuration option on the current server.</span></span> <span data-ttu-id="63e1f-150">此範例會傳回選項的名稱 (`name`) 和描述 (`description`)，以及選項是否為進階選項 (`is_advanced`)。</span><span class="sxs-lookup"><span data-stu-id="63e1f-150">The example returns the name (`name`) and description (`description`) of the option and whether the option is an advanced option (`is_advanced`).</span></span>  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a><span data-ttu-id="63e1f-151">使用 sp_configure 變更伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-151">To change a server property by using sp_configure</span></span>  
  
1.  <span data-ttu-id="63e1f-152">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63e1f-153">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63e1f-154">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63e1f-155">這個範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 變更伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="63e1f-155">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to change a server property.</span></span> <span data-ttu-id="63e1f-156">此範例會將 `fill factor` 選項的值變更為 `100`。</span><span class="sxs-lookup"><span data-stu-id="63e1f-156">The example changes the value of the `fill factor` option to `100`.</span></span> <span data-ttu-id="63e1f-157">伺服器必須重新啟動，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="63e1f-157">The server must be restarted before the change can take effect.</span></span>  
  
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
  
 <span data-ttu-id="63e1f-158">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="63e1f-158">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="63e1f-159">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="63e1f-159">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="63e1f-160">部分伺服器屬性可以使用 SQL Server 組態管理員檢視或變更。</span><span class="sxs-lookup"><span data-stu-id="63e1f-160">Some server properties can be viewed or changed by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="63e1f-161">例如，您可以檢視 SQL Server 執行個體的版本和版別，或是變更錯誤記錄檔儲存的位置。</span><span class="sxs-lookup"><span data-stu-id="63e1f-161">For example, you can view the version and edition of the instance of SQL Server, or change the location where error log files are stored.</span></span> <span data-ttu-id="63e1f-162">您也可以藉由查詢 [伺服器相關的動態管理檢視與函數](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)的方式檢視這些屬性。</span><span class="sxs-lookup"><span data-stu-id="63e1f-162">These properties can also be viewed by querying the [Server-Related Dynamic Management Views and Functions](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="63e1f-163">檢視或變更伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="63e1f-163">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="63e1f-164">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-164">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="63e1f-165">在 **[SQL Server 組態管理員]** 中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="63e1f-165">In **SQL Server Configuration Manager**, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="63e1f-166">在詳細資料窗格中，以滑鼠右鍵按一下 [SQL Server (\<***instancename***>)]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-166">In the details pane, right-click **SQL Server (\<***instancename***>)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="63e1f-167">在 [SQL Server (\<***instancename***>) 屬性] 對話方塊中，變更 [服務] 索引標籤或 [進階] 索引標籤上的伺服器屬性，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="63e1f-167">In the **SQL Server (\<***instancename***>) Properties** dialog box, change the server properties on the **Service** tab or the **Advanced** tab, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a><span data-ttu-id="63e1f-168">待處理：變更伺服器屬性之後</span><span class="sxs-lookup"><span data-stu-id="63e1f-168">Follow Up: After you change server properties</span></span>  
 <span data-ttu-id="63e1f-169">對於某些屬性，伺服器可能必須重新啟動，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="63e1f-169">For some properties, the server might have to be restarted before the change can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e1f-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e1f-170">See Also</span></span>  
 <span data-ttu-id="63e1f-171">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63e1f-171">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="63e1f-172">[SET 陳述式 &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-172">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 <span data-ttu-id="63e1f-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="63e1f-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="63e1f-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="63e1f-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="63e1f-177">[設定 WMI 在 SQL Server 工具中顯示伺服器狀態](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span><span class="sxs-lookup"><span data-stu-id="63e1f-177">[Configure WMI to Show Server Status in SQL Server Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span></span>  
 <span data-ttu-id="63e1f-178">[SQL Server 組態管理員](../../relational-databases/sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="63e1f-178">[SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="63e1f-179">[組態函式 &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63e1f-179">[Configuration Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span></span>  
 [<span data-ttu-id="63e1f-180">伺服器相關的動態管理檢視和函式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63e1f-180">Server-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
