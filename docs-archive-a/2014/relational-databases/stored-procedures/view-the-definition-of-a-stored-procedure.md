---
title: 檢視預存程序的定義 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4da455d38f984b08ee1f396f26cd4cc85411be92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595880"
---
# <a name="view-the-definition-of-a-stored-procedure"></a><span data-ttu-id="bd11a-102">檢視預存程序的定義</span><span class="sxs-lookup"><span data-stu-id="bd11a-102">View the Definition of a Stored Procedure</span></span>
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a> <span data-ttu-id="bd11a-103">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用 [物件總管] 功能表選項，或在查詢編輯器中使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]，檢視預存程序的定義。</span><span class="sxs-lookup"><span data-stu-id="bd11a-103">You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bd11a-104">本主題描述如何在 [物件總管] 中，以及透過系統預存程序、系統函數和查詢編輯器中的物件目錄檢視，來檢視程序的定義。</span><span class="sxs-lookup"><span data-stu-id="bd11a-104">This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.</span></span>  
  
-   <span data-ttu-id="bd11a-105">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="bd11a-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="bd11a-106">**若要檢視程序中的定義，使用：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="bd11a-106">**To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd11a-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="bd11a-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd11a-108">Security</span><span class="sxs-lookup"><span data-stu-id="bd11a-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bd11a-109">權限</span><span class="sxs-lookup"><span data-stu-id="bd11a-109">Permissions</span></span>  
 <span data-ttu-id="bd11a-110">系統預存程序：`sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="bd11a-110">System Stored Procedure: `sp_helptext`</span></span>  
 <span data-ttu-id="bd11a-111">需要 **public** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="bd11a-111">Requires membership in the **public** role.</span></span> <span data-ttu-id="bd11a-112">系統物件定義是公開顯示的。</span><span class="sxs-lookup"><span data-stu-id="bd11a-112">System object definitions are publicly visible.</span></span> <span data-ttu-id="bd11a-113">凡具有下列任一權限的物件擁有者或承授者，都看得到使用者物件的定義：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="bd11a-113">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span>  
  
 <span data-ttu-id="bd11a-114">系統函數：`OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="bd11a-114">System Function: `OBJECT_DEFINITION`</span></span>  
 <span data-ttu-id="bd11a-115">系統物件定義是公開顯示的。</span><span class="sxs-lookup"><span data-stu-id="bd11a-115">System object definitions are publicly visible.</span></span> <span data-ttu-id="bd11a-116">凡具有下列任一權限的物件擁有者或承授者，都看得到使用者物件的定義：ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="bd11a-116">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="bd11a-117">**db_owner**、 **db_ddladmin**和 **db_securityadmin** 固定資料庫角色的成員隱含地擁有這些權限。</span><span class="sxs-lookup"><span data-stu-id="bd11a-117">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="bd11a-118">物件目錄檢視：`sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="bd11a-118">Object Catalog View: `sys.sql_modules`</span></span>  
 <span data-ttu-id="bd11a-119">目錄檢視內中繼資料的可見性會限制在使用者所擁有的安全性實體，或已授與使用者某些權限的安全性實體。</span><span class="sxs-lookup"><span data-stu-id="bd11a-119">The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="bd11a-120">如需相關資訊，請參閱 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="bd11a-120">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="bd11a-121">如何檢視預存程序的定義</span><span class="sxs-lookup"><span data-stu-id="bd11a-121">How to View the Definition of a Stored Procedure</span></span>  
 <span data-ttu-id="bd11a-122">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bd11a-122">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="bd11a-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd11a-123">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="bd11a-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd11a-124">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd11a-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd11a-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bd11a-126">**在物件總管中檢視程序的定義**</span><span class="sxs-lookup"><span data-stu-id="bd11a-126">**To view the definition a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="bd11a-127">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd11a-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bd11a-128">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="bd11a-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="bd11a-129">展開 [預存程序]，以滑鼠右鍵按一下程序，然後按一下 [產生預存程序的指令碼為]，然後按一下下列其中一個項目：[建立為]、[變更為] 或 [DROP 並 CREATE 至]。</span><span class="sxs-lookup"><span data-stu-id="bd11a-129">Expand **Stored Procedures**, right-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.</span></span>  
  
4.  <span data-ttu-id="bd11a-130">選取 [新增查詢編輯器視窗]。</span><span class="sxs-lookup"><span data-stu-id="bd11a-130">Select **New Query Editor Window**.</span></span> <span data-ttu-id="bd11a-131">這會顯示程序定義。</span><span class="sxs-lookup"><span data-stu-id="bd11a-131">This will display the procedure definition.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bd11a-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd11a-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="bd11a-133">**在查詢編輯器中檢視程序的定義**</span><span class="sxs-lookup"><span data-stu-id="bd11a-133">**To view the definition of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="bd11a-134">系統預存程序：`sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="bd11a-134">System Stored Procedure: `sp_helptext`</span></span>  
 1.  <span data-ttu-id="bd11a-135">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd11a-135">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd11a-136">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="bd11a-136">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd11a-137">在查詢視窗中，輸入下列使用 `sp_helptext` 系統預存程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="bd11a-137">In the query window, enter the following statement that uses the `sp_helptext` system stored procedure.</span></span> <span data-ttu-id="bd11a-138">請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。</span><span class="sxs-lookup"><span data-stu-id="bd11a-138">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 <span data-ttu-id="bd11a-139">系統函數：`OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="bd11a-139">System Function: `OBJECT_DEFINITION`</span></span>  
 1.  <span data-ttu-id="bd11a-140">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd11a-140">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd11a-141">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="bd11a-141">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd11a-142">在查詢視窗中，輸入下列使用 `OBJECT_DEFINITION` 系統函數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="bd11a-142">In the query window, enter the following statements that use the `OBJECT_DEFINITION` system function.</span></span> <span data-ttu-id="bd11a-143">請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。</span><span class="sxs-lookup"><span data-stu-id="bd11a-143">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 <span data-ttu-id="bd11a-144">物件目錄檢視：`sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="bd11a-144">Object Catalog View: `sys.sql_modules`</span></span>  
 1.  <span data-ttu-id="bd11a-145">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd11a-145">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd11a-146">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="bd11a-146">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd11a-147">在查詢視窗中，輸入下列使用 `sys.sql_modules` 目錄檢視的陳述式。</span><span class="sxs-lookup"><span data-stu-id="bd11a-147">In the query window, enter the following statements that use the `sys.sql_modules` catalog view.</span></span> <span data-ttu-id="bd11a-148">請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。</span><span class="sxs-lookup"><span data-stu-id="bd11a-148">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bd11a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd11a-149">See Also</span></span>  
 <span data-ttu-id="bd11a-150">[建立預存程序](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bd11a-150">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="bd11a-151">[修改預存程序](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bd11a-151">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="bd11a-152">[刪除預存程序](delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bd11a-152">[Delete a Stored Procedure](delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="bd11a-153">[重新命名預存程序](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bd11a-153">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="bd11a-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd11a-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span></span>  
 <span data-ttu-id="bd11a-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd11a-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="bd11a-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd11a-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span></span>  
 [<span data-ttu-id="bd11a-157">OBJECT_ID &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bd11a-157">OBJECT_ID &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-id-transact-sql)  
  
  
