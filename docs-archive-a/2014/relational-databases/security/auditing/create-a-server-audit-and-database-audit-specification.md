---
title: 建立伺服器稽核和資料庫稽核規格 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cad01eae45d534f0f74911ce8f57827858cc920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700966"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a><span data-ttu-id="29d46-102">建立伺服器稽核和資料庫稽核規格</span><span class="sxs-lookup"><span data-stu-id="29d46-102">Create a Server Audit and Database Audit Specification</span></span>
  <span data-ttu-id="29d46-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立伺服器稽核和資料庫稽核規格。</span><span class="sxs-lookup"><span data-stu-id="29d46-103">This topic describes how to create a server audit and database audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="29d46-104">*「稽核」* (Audit) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的執行個體牽涉到追蹤和記錄系統上所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="29d46-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="29d46-105">*SQL Server Audit* 物件會收集要監視之伺服器或資料庫層級動作和動作群組的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="29d46-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="29d46-106">此稽核位於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體層級。</span><span class="sxs-lookup"><span data-stu-id="29d46-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="29d46-107">您可以針對每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體設有多個稽核。</span><span class="sxs-lookup"><span data-stu-id="29d46-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="29d46-108">「資料庫層級稽核規格」  物件屬於稽核。</span><span class="sxs-lookup"><span data-stu-id="29d46-108">The *Database-Level Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="29d46-109">您可以針對每個稽核的每個 SQL Server 資料庫建立一個資料庫稽核規格。</span><span class="sxs-lookup"><span data-stu-id="29d46-109">You can create one database audit specification per SQL Server database per audit.</span></span> <span data-ttu-id="29d46-110">如需詳細資訊，請參閱 [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="29d46-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="29d46-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="29d46-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="29d46-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="29d46-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="29d46-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="29d46-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="29d46-114">安全性</span><span class="sxs-lookup"><span data-stu-id="29d46-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="29d46-115">**若要使用下列項目建立伺服器稽核和資料庫稽核規格：**</span><span class="sxs-lookup"><span data-stu-id="29d46-115">**To create a server audit and database audit specification, using:**</span></span>  
  
     [<span data-ttu-id="29d46-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="29d46-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="29d46-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="29d46-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="29d46-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="29d46-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="29d46-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="29d46-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="29d46-120">資料庫稽核規格是位於給定資料庫內的非安全性實體物件。</span><span class="sxs-lookup"><span data-stu-id="29d46-120">Database audit specifications are non-securable objects that reside in a given database.</span></span> <span data-ttu-id="29d46-121">當建立資料庫稽核規格之後，它就會處於停用狀態。</span><span class="sxs-lookup"><span data-stu-id="29d46-121">When a database audit specification is created, it is in a disabled state.</span></span>  
  
 <span data-ttu-id="29d46-122">當您在使用者資料庫中建立或修改資料庫稽核規格時，請勿在伺服器範圍的物件 (如系統檢視) 上包含稽核動作。</span><span class="sxs-lookup"><span data-stu-id="29d46-122">When you are creating or modifying a database audit specification in a user database, do not include audit actions on server-scope objects, such as the system views.</span></span> <span data-ttu-id="29d46-123">如果包含了伺服器範圍的物件，將會建立稽核。</span><span class="sxs-lookup"><span data-stu-id="29d46-123">If server-scoped objects are included, the audit will be created.</span></span> <span data-ttu-id="29d46-124">但是，將不會包含伺服器範圍的物件，而且不會傳回任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="29d46-124">However, the server-scoped objects will not be included, and no error will be returned.</span></span> <span data-ttu-id="29d46-125">若要稽核伺服器範圍的物件，請在 master 資料庫中使用資料庫稽核規格。</span><span class="sxs-lookup"><span data-stu-id="29d46-125">To audit server-scope objects, use a database audit specification in the master database.</span></span>  
  
 <span data-ttu-id="29d46-126">資料庫稽核規格位於其建立所在的資料庫，但是 `tempdb` 系統資料庫除外。</span><span class="sxs-lookup"><span data-stu-id="29d46-126">Database audit specifications reside in the database where they are created, with the exception of the `tempdb` system database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="29d46-127">Security</span><span class="sxs-lookup"><span data-stu-id="29d46-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="29d46-128">權限</span><span class="sxs-lookup"><span data-stu-id="29d46-128">Permissions</span></span>  
  
-   <span data-ttu-id="29d46-129">具有 ALTER ANY DATABASE AUDIT 權限的使用者可以建立資料庫稽核規格，並將其繫結至任何稽核。</span><span class="sxs-lookup"><span data-stu-id="29d46-129">Users with the ALTER ANY DATABASE AUDIT permission can create database audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="29d46-130">在建立資料庫稽核規格之後，具有 CONTROL SERVER 或 ALTER ANY DATABASE AUDIT 權限的主體，或是系統管理員帳戶將可以檢視此規格。</span><span class="sxs-lookup"><span data-stu-id="29d46-130">After a database audit specification is created, it can be viewed by principals with the CONTROL SERVER,  ALTER ANY DATABASE AUDIT permissions, or the sysadmin account.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="29d46-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="29d46-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="29d46-132">若要建立伺服器稽核</span><span class="sxs-lookup"><span data-stu-id="29d46-132">To create a server audit</span></span>  
  
1.  <span data-ttu-id="29d46-133">在 [物件總管] 中，展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29d46-133">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="29d46-134">以滑鼠右鍵按一下 [**審核**] 資料夾，然後選取 [新增] [ **Audit**...]。如需詳細資訊，請參閱[建立伺服器 audit 和伺服器 Audit 規格](create-a-server-audit-and-server-audit-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="29d46-134">Right-click the **Audits** folder and select **New Audit...**. For more information, see [Create a Server Audit and Server Audit Specification](create-a-server-audit-and-server-audit-specification.md).</span></span>  
  
3.  <span data-ttu-id="29d46-135">當您完成選取選項之後，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="29d46-135">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="29d46-136">若要建立資料庫層級的稽核規格</span><span class="sxs-lookup"><span data-stu-id="29d46-136">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="29d46-137">在 [物件總管] 中，展開您要建立稽核規格的資料庫。</span><span class="sxs-lookup"><span data-stu-id="29d46-137">In Object Explorer, expand the database where you want to create an audit specification.</span></span>  
  
2.  <span data-ttu-id="29d46-138">展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29d46-138">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="29d46-139">以滑鼠右鍵按一下 [**資料庫 Audit 規格**] 資料夾，然後選取 [**新增資料庫] [audit 規格**...]。</span><span class="sxs-lookup"><span data-stu-id="29d46-139">Right-click the **Database Audit Specifications** folder and select **New Database Audit Specification...**.</span></span>  
  
     <span data-ttu-id="29d46-140">**[建立資料庫稽核規格]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="29d46-140">The following options are available on the **Create Database Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="29d46-141">**名稱**</span><span class="sxs-lookup"><span data-stu-id="29d46-141">**Name**</span></span>  
     <span data-ttu-id="29d46-142">資料庫稽核規格的名稱。</span><span class="sxs-lookup"><span data-stu-id="29d46-142">The name of the database audit specification.</span></span> <span data-ttu-id="29d46-143">當您建立新的伺服器稽核規格時會自動產生這個名稱，但是可加以編輯。</span><span class="sxs-lookup"><span data-stu-id="29d46-143">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="29d46-144">**稽核**</span><span class="sxs-lookup"><span data-stu-id="29d46-144">**Audit**</span></span>  
     <span data-ttu-id="29d46-145">現有資料庫稽核規格的名稱。</span><span class="sxs-lookup"><span data-stu-id="29d46-145">The name of an existing database audit.</span></span> <span data-ttu-id="29d46-146">請輸入稽核名稱或從清單中選取。</span><span class="sxs-lookup"><span data-stu-id="29d46-146">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="29d46-147">**稽核動作類型**</span><span class="sxs-lookup"><span data-stu-id="29d46-147">**Audit Action Type**</span></span>  
     <span data-ttu-id="29d46-148">指定要擷取之資料庫層級的稽核動作群組和稽核動作。</span><span class="sxs-lookup"><span data-stu-id="29d46-148">Specifies the database-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="29d46-149">如需資料庫層級稽核動作群組和稽核動作的清單以及其所包含的事件描述，請參閱 [SQL Server Audit 動作群組和動作](sql-server-audit-action-groups-and-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="29d46-149">For the list of database-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="29d46-150">**物件結構描述**</span><span class="sxs-lookup"><span data-stu-id="29d46-150">**Object Schema**</span></span>  
     <span data-ttu-id="29d46-151">顯示指定之 [物件名稱]  的結構描述。</span><span class="sxs-lookup"><span data-stu-id="29d46-151">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="29d46-152">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="29d46-152">**Object Name**</span></span>  
     <span data-ttu-id="29d46-153">要稽核的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="29d46-153">The name of the object to audit.</span></span> <span data-ttu-id="29d46-154">這只適用於稽核動作，不適用於稽核群組。</span><span class="sxs-lookup"><span data-stu-id="29d46-154">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="29d46-155">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="29d46-155">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="29d46-156">開啟 **[選取物件]** 對話方塊來瀏覽及選取可用的物件 (根據指定的 **[稽核動作類型]** )。</span><span class="sxs-lookup"><span data-stu-id="29d46-156">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="29d46-157">**主體名稱**</span><span class="sxs-lookup"><span data-stu-id="29d46-157">**Principal Name**</span></span>  
     <span data-ttu-id="29d46-158">依據所稽核的物件來篩選稽核的帳戶。</span><span class="sxs-lookup"><span data-stu-id="29d46-158">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="29d46-159">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="29d46-159">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="29d46-160">開啟 **[選取物件]** 對話方塊來瀏覽及選取可用的物件 (根據指定的 **[物件名稱]** )。</span><span class="sxs-lookup"><span data-stu-id="29d46-160">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
4.  <span data-ttu-id="29d46-161">當您完成選取選項之後，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="29d46-161">When you are finished selecting option, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="29d46-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="29d46-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="29d46-163">若要建立伺服器稽核</span><span class="sxs-lookup"><span data-stu-id="29d46-163">To create a server audit</span></span>  
  
1.  <span data-ttu-id="29d46-164">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29d46-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="29d46-165">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="29d46-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="29d46-166">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="29d46-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="29d46-167">若要建立資料庫層級的稽核規格</span><span class="sxs-lookup"><span data-stu-id="29d46-167">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="29d46-168">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29d46-168">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="29d46-169">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="29d46-169">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="29d46-170">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="29d46-170">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="29d46-171">範例會針對 `Audit_Pay_Tables` 資料表 (以上方定義的伺服器稽核為基礎)，建立可稽核 `dbo` 使用者所執行 SELECT 和 INSERT 陳述式的資料庫稽核規格，其名稱為 `HumanResources.EmployeePayHistory` 。</span><span class="sxs-lookup"><span data-stu-id="29d46-171">The example creates a database audit specification called `Audit_Pay_Tables` that audits SELECT and INSERT statements by the `dbo` user, for the `HumanResources.EmployeePayHistory` table based on the server audit defined above.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 <span data-ttu-id="29d46-172">如需詳細資訊，請參閱 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) 和 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="29d46-172">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql).</span></span>  
  
  
