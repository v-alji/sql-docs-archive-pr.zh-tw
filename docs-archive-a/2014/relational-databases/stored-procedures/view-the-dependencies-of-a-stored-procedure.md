---
title: 檢視預存程序的相依性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 790684035d2db3b697fb8b718c96182eda8f1186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607351"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a><span data-ttu-id="8f1fa-102">檢視預存程序的相依性</span><span class="sxs-lookup"><span data-stu-id="8f1fa-102">View the Dependencies of a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="8f1fa-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 來檢視 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的預存程序相依性。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-103">This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="8f1fa-104">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="8f1fa-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="8f1fa-105">**若要檢視程序的相依性，請使用：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="8f1fa-105">**To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8f1fa-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="8f1fa-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8f1fa-107">Security</span><span class="sxs-lookup"><span data-stu-id="8f1fa-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8f1fa-108">權限</span><span class="sxs-lookup"><span data-stu-id="8f1fa-108">Permissions</span></span>  
 <span data-ttu-id="8f1fa-109">系統函數：`sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-109">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="8f1fa-110">需要受參考實體的 CONTROL 權限和 sys.dm_sql_referencing_entities 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-110">Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm_sql_referencing_entities.</span></span> <span data-ttu-id="8f1fa-111">當受參考實體為資料分割函數時，便需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-111">When the referenced entity is a partition function, CONTROL permission on the database is required.</span></span> <span data-ttu-id="8f1fa-112">根據預設，SELECT 權限會授與 public。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-112">By default, SELECT permission is granted to public.</span></span>  
  
 <span data-ttu-id="8f1fa-113">系統函數：`sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-113">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="8f1fa-114">需要 sys.dm_sql_referenced_entities 的 SELECT 權限和參考實體的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-114">Requires SELECT permission on sys.dm_sql_referenced_entities and VIEW DEFINITION permission on the referencing entity.</span></span> <span data-ttu-id="8f1fa-115">根據預設，SELECT 權限會授與 public。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-115">By default, SELECT permission is granted to public.</span></span> <span data-ttu-id="8f1fa-116">當參考實體為資料庫層級 DDL 觸發程序時，便需要資料庫的 VIEW DEFINITION 權限，或資料庫的 ALTER DATABASE DDL TRIGGER 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-116">Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database-level DDL trigger.</span></span> <span data-ttu-id="8f1fa-117">當參考實體為伺服器層級 DDL 觸發程序時，便需要伺服器的 VIEW ANY DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-117">Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server-level DDL trigger.</span></span>  
  
 <span data-ttu-id="8f1fa-118">物件目錄檢視：`sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-118">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="8f1fa-119">需要資料庫的 VIEW DEFINITION 權限和資料庫之 sys.sql_expression_dependencies 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-119">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="8f1fa-120">根據預設，SELECT 權限只授與 db_owner 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-120">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="8f1fa-121">當 SELECT 和 VIEW DEFINITION 權限授與其他使用者時，被授與者就可以檢視資料庫中的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-121">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="8f1fa-122">如何檢視預存程序的相依性</span><span class="sxs-lookup"><span data-stu-id="8f1fa-122">How to View the Dependencies of a Stored Procedure</span></span>  
 <span data-ttu-id="8f1fa-123">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8f1fa-123">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="8f1fa-124">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8f1fa-124">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="8f1fa-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8f1fa-125">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8f1fa-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8f1fa-126">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8f1fa-127">**在物件總管中檢視程序的相依性**</span><span class="sxs-lookup"><span data-stu-id="8f1fa-127">**To view the dependencies of a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="8f1fa-128">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-128">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8f1fa-129">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-129">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="8f1fa-130">展開 [預存程序]，以滑鼠右鍵按一下程序，然後按一下 [檢視相依性]。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-130">Expand **Stored Procedures**, right-click the procedure and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="8f1fa-131">檢視相依於程序的物件清單。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-131">View the list of objects that depend on the procedure.</span></span>  
  
5.  <span data-ttu-id="8f1fa-132">檢視程序所相依的物件清單。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-132">View the list of objects on which the procedure depends.</span></span>  
  
6.  <span data-ttu-id="8f1fa-133">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-133">Click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8f1fa-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8f1fa-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="8f1fa-135">**在查詢編輯器中檢視程序的相依性**</span><span class="sxs-lookup"><span data-stu-id="8f1fa-135">**To view the dependencies of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="8f1fa-136">系統函數：`sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-136">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="8f1fa-137">此函數用來顯示相依於程序的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-137">This function is used to display the objects that depend on a procedure.</span></span>  
  
1.  <span data-ttu-id="8f1fa-138">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8f1fa-139">展開 **[資料庫]** ，展開程序所屬的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-139">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="8f1fa-140">按一下 **[檔案]** 功能表下的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-140">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="8f1fa-141">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-141">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="8f1fa-142">第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-142">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="8f1fa-143">建立程序之後，第二個範例會使用 sys.dm_sql_referencing_entities 函數顯示相依於程序的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-143">After the procedure is created, the second example uses the sys.dm_sql_referencing_entities function to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 <span data-ttu-id="8f1fa-144">系統函數：`sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-144">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="8f1fa-145">此函數用來顯示程序所相依的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-145">This function is used to display the objects a procedure depends on.</span></span>  
  
1.  <span data-ttu-id="8f1fa-146">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-146">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8f1fa-147">展開 **[資料庫]** ，展開程序所屬的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-147">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="8f1fa-148">按一下 **[檔案]** 功能表下的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-148">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="8f1fa-149">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-149">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="8f1fa-150">第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-150">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="8f1fa-151">建立程序之後，第二個範例會使用 sys.dm_sql_referenced_entities 函數顯示程序相依的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-151">After the procedure is created, the second example uses the sys.dm_sql_referenced_entities function to display the objects that the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 <span data-ttu-id="8f1fa-152">物件目錄檢視：`sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="8f1fa-152">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="8f1fa-153">此檢視可用來顯示程序相依的物件或相依於程序的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-153">This view can be used to display objects that a procedure depends on or that depend on a procedure.</span></span>  
  
 <span data-ttu-id="8f1fa-154">顯示相依於程序的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-154">Displaying the objects that depend on a procedure.</span></span>  
 1.  <span data-ttu-id="8f1fa-155">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8f1fa-156">展開 **[資料庫]** ，展開程序所屬的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-156">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="8f1fa-157">按一下 **[檔案]** 功能表下的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-157">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="8f1fa-158">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-158">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="8f1fa-159">第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-159">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="8f1fa-160">建立程序之後，第二個範例會使用 sys.sql_expression_dependencies 檢視顯示相依於程序的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-160">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 <span data-ttu-id="8f1fa-161">顯示程序所相依的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-161">Displaying the objects a procedure depends on.</span></span>  
 1.  <span data-ttu-id="8f1fa-162">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8f1fa-163">展開 **[資料庫]** ，展開程序所屬的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-163">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="8f1fa-164">按一下 **[檔案]** 功能表下的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-164">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="8f1fa-165">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-165">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="8f1fa-166">第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-166">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="8f1fa-167">建立程序之後，第二個範例會使用 sys.sql_expression_dependencies 檢視顯示程序相依的物件。</span><span class="sxs-lookup"><span data-stu-id="8f1fa-167">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8f1fa-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f1fa-168">See Also</span></span>  
 <span data-ttu-id="8f1fa-169">[重新命名預存程序](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="8f1fa-169">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="8f1fa-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f1fa-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span></span>  
 <span data-ttu-id="8f1fa-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f1fa-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span></span>  
 [<span data-ttu-id="8f1fa-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f1fa-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
