---
title: 重新命名預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02e1acb528a32ef242e160e0ce5dd0267237c876
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607356"
---
# <a name="rename-a-stored-procedure"></a><span data-ttu-id="6c2ad-102">重新命名預存程序</span><span class="sxs-lookup"><span data-stu-id="6c2ad-102">Rename a Stored Procedure</span></span>
  <span data-ttu-id="6c2ad-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 重新命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-103">This topic describes how to rename a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6c2ad-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6c2ad-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6c2ad-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6c2ad-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6c2ad-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="6c2ad-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6c2ad-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6c2ad-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6c2ad-108">**若要重新命名預存程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="6c2ad-108">**To rename a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="6c2ad-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c2ad-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6c2ad-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c2ad-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c2ad-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="6c2ad-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6c2ad-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="6c2ad-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6c2ad-113">程序名稱必須符合 [識別碼](../databases/database-identifiers.md)的規則。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-113">Procedure names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="6c2ad-114">重新命名預存程序不會變更 **sys.sql_modules** 目錄檢視 definition 資料行中對應的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-114">Renaming a stored procedure will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="6c2ad-115">因此，我們建議您不要重新命名這個物件類型。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="6c2ad-116">相反地，請卸除預存程序，再利用它的新名稱來重新建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="6c2ad-117">變更程序的名稱或定義後，若未更新物件來反映對程序所做的變更，則可能導致相依物件執行失敗。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-117">Changing the name or definition of a procedure can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the procedure.</span></span> <span data-ttu-id="6c2ad-118">如需詳細資訊，請參閱 [檢視預存程序的相依性](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-118">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c2ad-119">Security</span><span class="sxs-lookup"><span data-stu-id="6c2ad-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c2ad-120">權限</span><span class="sxs-lookup"><span data-stu-id="6c2ad-120">Permissions</span></span>  
 <span data-ttu-id="6c2ad-121">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="6c2ad-121">CREATE PROCEDURE</span></span>  
 <span data-ttu-id="6c2ad-122">需要資料庫的 CREATE PROCEDURE 權限，以及要在其中建立程序之結構描述的 ALTER 權限，或者需要 **db_ddladmin** 固定資料庫角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-122">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created, or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
 <span data-ttu-id="6c2ad-123">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="6c2ad-123">ALTER PROCEDURE</span></span>  
 <span data-ttu-id="6c2ad-124">需要程序的 ALTER 權限，或 **db_ddladmin** 固定資料庫角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-124">Requires ALTER permission on the procedure or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6c2ad-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c2ad-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="6c2ad-126">若要重新命名預存程序</span><span class="sxs-lookup"><span data-stu-id="6c2ad-126">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="6c2ad-127">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="6c2ad-128">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="6c2ad-129">[判斷預存程序的相依性](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-129">[Determine the dependencies of the stored procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
4.  <span data-ttu-id="6c2ad-130">展開 [預存程序]，以滑鼠右鍵按一下要重新命名的程序，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-130">Expand **Stored Procedures**, right-click the procedure to rename, and then click **Rename**.</span></span>  
  
5.  <span data-ttu-id="6c2ad-131">修改程序名稱。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-131">Modify the procedure name.</span></span>  
  
6.  <span data-ttu-id="6c2ad-132">修改在任何相依物件或指令碼中參考的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-132">Modify the procedure name referenced in any dependent objects or scripts.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6c2ad-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c2ad-133">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="6c2ad-134">若要重新命名預存程序</span><span class="sxs-lookup"><span data-stu-id="6c2ad-134">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="6c2ad-135">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c2ad-136">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c2ad-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6c2ad-138">這個範例示範如何藉由卸除程序，再以新名稱重新建立程序的方式重新命名程序。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-138">This example shows how to rename a procedure by dropping the procedure and re-creating the procedure with a new name.</span></span> <span data-ttu-id="6c2ad-139">第一個範例會建立 `'HumanResources.uspGetAllEmployeesTest`預存程序。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-139">The first example creates the stored procedure `'HumanResources.uspGetAllEmployeesTest`.</span></span> <span data-ttu-id="6c2ad-140">第二個範例會將預存程序重新命名為 `HumanResources.uspEveryEmployeeTest`。</span><span class="sxs-lookup"><span data-stu-id="6c2ad-140">The second example renames the stored procedure to `HumanResources.uspEveryEmployeeTest`.</span></span>  
  
```sql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c2ad-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2ad-141">See Also</span></span>  
 <span data-ttu-id="6c2ad-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span></span>  
 <span data-ttu-id="6c2ad-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="6c2ad-144">[建立預存程序](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6c2ad-145">[修改預存程序](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-145">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6c2ad-146">[刪除預存程序](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="6c2ad-147">[檢視預存程序的定義](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="6c2ad-147">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="6c2ad-148">檢視預存程序的相依性</span><span class="sxs-lookup"><span data-stu-id="6c2ad-148">View the Dependencies of a Stored Procedure</span></span>](view-the-dependencies-of-a-stored-procedure.md)  
  
  
